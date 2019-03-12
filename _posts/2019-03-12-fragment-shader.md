---
published: true
---
Fragment shader fonksiyonu da vertex shader’a oldukça benzerdir. Texture koordinatları ve üretilmiş fragmentin rengini alır. Bu noktada pozisyona ihtiyaç yoktur. Grafik kart çoktan fragment’in hesaplanmış hücresel pozisyonuna sahiptir. Yine de texture’lanmış varlıklarla çalışıyorsanız mevcut texture’a ihtiyacınız vardır.

_uniform sampler2D texture;

void main()
{
    // lookup the pixel in the texture
    vec4 pixel = texture2D(texture, glTexCoord[0].xy);

    // multiply it by the color
    glFragColor = glColor * pixel;
}_

Mevcut texture otomatik değildir. Diğer girdi değişkenlerini işleme almanız gerekir. Ayrıca açık bir şekilde c++ programınızdan almanız icap eder. Programınızda bütün varlıklar farklı texture’a sahip olabilir. Daha da kötüsü bunları shader’a aktarmanın bir yolu olmayabilir. Bu tarz durumlar için SFML, setUniform fonksiyonuna overload yapmanıza izin verir. 

shader.setUniform("texture", sf::Shader::CurrentTexture);

Bu özel parametre varlığın texture’ını otomatik ayarlar ve çizimde shader değişkenine isim verir. Siz her yeni varlık çizdiğinizde SFML shader texture değişkenlerini uygun olarak güncelleyecektir.
