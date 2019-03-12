---
published: true
---
## Özel Transformlar

sf::Transformable sınıfı kullanımı kolay fakat sınırlı bir sınıf. Bazı kullanıcılar daha fazla esneklik isteyebilirler. Son transformasyonu özelleştirmek isteyebilirler. Bu tarz şeylere ihtiyaç duyan kullanıcılar için daha düşük seviye (low-level) bir sınıf mevcut: sf::Transform. Bu sınıf esasında 3x3’lük bir matirsten daha fazlası değil. Dolayısıyla istediğiniz herhangi bir şekili 2D uzayda sunabilirsiniz. 
sf::Transform sınıfını yapılandırmanın birden fazla yolu mevcut:
    • Sık kullanılan transformlar (rotasyon vs.) için ön tanımlı fonksiyonlar kulllanabilirsiniz. 
    • İki transformu kombine edebilirsiniz.
    • 9 elemanı doğrudan belirtebilirsiniz. 
Aşağıda birkaç örnek sunuyoruz:

// the identity transform (does nothing)
sf::Transform t1 = sf::Transform::Identity;

// a rotation transform
sf::Transform t2;
t2.rotate(45.f);

// a custom matrix
sf::Transform t3(2.f, 0.f, 20.f,
                 0.f, 1.f, 50.f,
                 0.f, 0.f, 1.f);

// a combined transform
sf::Transform t4 = t1 * t2 * t3;

Birden fazla transformu ön tanımlı olarak aynı transforma uygulayabilirsiniz. Sıralı bir şekilde kombine olacaklardır.

sf::Transform t;
t.translate(10.f, 100.f);
t.rotate(90.f);
t.translate(-10.f, 50.f);
t.scale(0.5f, 0.75f);

Özel bir transform grafiksel bir varlık olarak nasıl uygulanır? Basit: draw fonksiyonunu kullanın. 

window.draw(entity, transform);

bunun için bir kısayol mevcut:

sf::RenderStates states;
states.transform = transform;
window.draw(entity, states);

Eğer sizin sf::Transformable varlığınız kendi dahili transformunu içeriyorsa Dahili ve geçici trasform finalde kombine edilecektir.
