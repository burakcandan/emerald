---
published: true
---
Varlıkları transform edip çizdikten sonra onların performansını ölçümlemek isteyebilirsiniz. Örnek vermek gerekirse çakışma olup olmadığına bakmak isteyebilirsiniz.

SFML varlıklarının boundinx boxları mevcuttur. Boundinx box yapısı x, y ekseninde varlıkların tüm noktalarını kapsayan minimal dikdörtgenlerdir. 

![1.png](sfml-dokumantasyon/_posts/1.png)

Bounding box yapısı çakışma kontrolünde çok kullanışlıdır. 

// get the bounding box of the entity
sf::FloatRect boundingBox = entity.getGlobalBounds();

// check collision with a point
sf::Vector2f point = ...;
if (boundingBox.contains(point))
{
    // collision!
}

// check collision with another box (like the bounding box of another entity)
sf::FloatRect otherBox = ...;
if (boundingBox.intersects(otherBox))
{
    // collision!
}


Fonksiyonun ismi getGlobalBounds çünkü varlığa ait bounding box global koordinat sistemine göre  dönüş yapar.  Buna ek olarak bir de getLocalBounds fonksiyonu mevcuttur. Bu fonksiyon da lokalde dönüş sağlar. Bu fonksiyon varlığın başlangıçtaki boyutunu elde etmede veya özel hesaplamalarda kullanılabilir.
