---
published: true
---
## Shader Yüklemek

SFML’de shader sf::Shader sınıfıyla temsil edilir. Bu sınıf hem vertex’i hem de fragmenti destekler. Sf::Shader ikisinin kombinasyonudur.
Eski grafik kartları Shader’ın bazı özelliklerini desteklemeyebilir. Programda ilk önce sistemde shader’ın kullanılabilir olup olmadığını kontrol edin. 

if (!sf::Shader::isAvailable())
{
    // shaders are not available...
}

Eğer sf::Shader::isAvailable() false durumdaysa sf::Shader sınıfını yürütmek mümkün olmayacaktır.
loadFromFile fonksiyonu diskten dosyaya shader yüklemenin en yaygın yoludur. 

sf::Shader shader;

// load only the vertex shader
if (!shader.loadFromFile("vertex_shader.vert", sf::Shader::Vertex))
{
    // error...
}

// load only the fragment shader

if (!shader.loadFromFile("fragment_shader.frag", sf::Shader::Fragment))
{
    // error...
}

// load both shaders
if (!shader.loadFromFile("vertex_shader.vert", "fragment_shader.frag"))
{
    // error...
}

shader kaynak kodları basit bir text dosyasının içinde tutulur (c++ kodları gibi). Dosya uzantısı çok önemli değildir. “.vert” veya “.frag” gibi mümkün olan uzantılardan herhangi biri olabilir.
Uyarı: loadFromFile fonksiyonu bazen belirli bir sebep olmadan hata verebilir. Böyle durumlarda dosya dizin yolunu veya ide kullanıyorsanız proje ayarlarını kontrol edin.

loadFromMemory fonksiyonu ile shaderları doğrudan stringlerden yükleyebilirsiniz. Bu yöntem kaynak kodlarınızı doğrudan programınıza gömmek istiyorsanız oldukça kullanışlıdır.

const std::string vertexShader = \
    "void main()" \
    "{" \
    "    ..." \
    "}";

const std::string fragmentShader = \
    "void main()" \
    "{" \
    "    ..." \
    "}";

// load only the vertex shader
if (!shader.loadFromMemory(vertexShader, sf::Shader::Vertex))
{

    // error...
}

// load only the fragment shader
if (!shader.loadFromMemory(fragmentShader, sf::Shader::Fragment))
{
    // error...
}

// load both shaders
if (!shader.loadFromMemory(vertexShader, fragmentShader))
{
    // error...
} 

elbette son olarak shader yüklemek için loadFromStream fonksiyonunu da kullanabilirsiniz.
