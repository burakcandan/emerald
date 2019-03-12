---
published: true
---
SFML, sf::Vertex yapısıyla vertex formatını düzenler. Bir SFML vertexi 2D pozisyonu, renk ve 2D texture koordinatlarını içerir. Bu yapı vertex shader’ında elde edilecek olan kesin girdidir. Vertex shadergl_Vertex, gl_Color ve gl_MultiTexCoord0 değişkenleri olarak depolanır ve yapılandırırlır.

void main()
{
    // transform the vertex position
    glPosition = glModelViewProjectionMatrix * glVertex;

    // transform the texture coordinates
    glTexCoord[0] = glTextureMatrix[0] * glMultiTexCoord0;

    // forward the vertex color
    glFrontColor = glColor;
}

Pozisyon genel olarak model-view ve matris projeksiyonları tarafından transform edilmeye ihtiyaç duyar, mevcut view varlık transformunu içerir. Texture koordinatları da texture matrisi tarafından transfrom edilmelidir. Sonuçta renk sadece iletilmelidir. Elbette texture koordinatlarını veya rengi görmezden gelebilirsiniz (kullanmadığınız taktirde). 
Bütün değişkenler, grafik kart tarafından ara değerler olarak ekli bir şekilde birincil üzerine işlenir ve fragment shader’a geçilir.
