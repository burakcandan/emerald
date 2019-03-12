---
published: true
---
## Değişkenden Shader’a geçiş

Diğer programlarda olduğu gibi shader parametre alabilir. Bu da şekil geçişlerini sağlar. Bu parametreler uniformlar olarak bilinirler ve global değişkenler olarak deklare edilmeledirler.

uniform float myvar;

void main()
{
    // use myvar...
}

Uniformlar C++ programı tarafından set edilebilirler. SetUniform fonksiyonunu çeşitli overloadlu halleriyle sf::Shader sınıfı içinde kullanmak bu tarz işlemler için yeterli.  

shader.setUniform("myvar", 5.f);

setUniform overload işlemi SFML tarafından sağlanmış tüm tipleri destekler:
    • float (GLSL type float)
    • 2 floats, sf::Vector2f (GLSL type vec2)
    • 3 floats, sf::Vector3f (GLSL type vec3)
    • 4 floats (GLSL type vec4)
    • sf::Color (GLSL type vec4)
    • sf::Transform (GLSL type mat4)
    • sf::Texture (GLSL type sampler2D)

Uyarı: GLSL compiler mekanizması kullanılmayan değişkenleri optimize edebilir (kullanılmayandan kasıt final vertexine/pikeseline  dahil edilmeyen hesaplamadır). Bundan dolayı setUniformu kullanırken şu tarz bir hata alırsanız şaşırmayın:”Failed to find variable "xxx" in shader”
