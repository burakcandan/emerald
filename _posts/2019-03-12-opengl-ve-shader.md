---
published: true
---
### OpenGL Kodu ve sf::Shader kullanımı

OpenGL kullanıyor olsanız da sf::Shader’ı kullanabilirsiniz. Çizim esnasında sf::Shader’ı aktif etmek için bind static fonksiyonuna başvurmanız gerekir.

_sf::Shader shader;
...

// bind the shader
sf::Shader::bind(&shader);

// draw your OpenGL entity here...

// bind no shader
sf::Shader::bind(NULL);_
