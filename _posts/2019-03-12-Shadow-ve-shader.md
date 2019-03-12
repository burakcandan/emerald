---
published: true
---
## Gölgelerle (Shader) özel efekt eklemek

Temelde gölge( shader diye kullanacağız yazının devamında) grafik kart üzerinde işlem gören küçük bir programdır. Bu durum programcıya çizim sürecinde daha fazla kontrol ve esneklik sağlar. Ek olarak durumları düzenlemede OpenGL destekli operasyonlarda kolay bir yoldur. Bu ek esneklik, shader kullanılarak oluşturulmuş efekt bazen komplike olabilir. Sıradan OpenGL fonksiyonlarını tanımlayabilirsiniz. Güncel grafik kartları ve OpenGL’İn yeni sürümleri shader temellidir. Durumları ve fonksiyonları düzenleyebilirsiniz (“fixed pipline”) elbette bunun modası geçmek üzer ve gelecekte kaldırılabilir.
Shaderlar, GLSL(OpenGL Shading Language)’de yazılmıştır. GLSL, C programlama diliyle oldukça benzerdir.   

Shader konusunda iki tip shader vardır:
    • Vertex shader
    • Fragment (piksel) shader

Vertex shaderları her bir vertex için işlem görürken, fragment shaderlar üretilmiş her fragment için işlem görür. Hangi tür shaderi kullanacağınız, elde etmek istediğiniz efekte göre değişebilir. Durum icap ederse her ikisini de kullanabilirsiniz. 

Hangi shader ne yapar ve nasıl etkili kullanılır konusunu iyi anlamak için pipeline render işlemi temellerini iyi anlamak çok önemli. Başlangıçta GLSL programı nasıl yazılır konusuna iyi bakmalısınız. SFML SDK ile gelen Shader örneğine de bakmanızda fayda var. 

Dökümanın bu bölümü sadece SFML’de shader nasıl uygulanır ve nasıl yüklenirle alaklı olacak. Shader yazımı konuya dahil değildir.
