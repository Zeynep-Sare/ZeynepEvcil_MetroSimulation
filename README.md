# ZeynepEvcil_MetroSimulation
1. Proje Başlığı ve Kısa Açıklama
Proje Sürücüsüz Metro Simülasyonudur ve bu projede, bir metro ağında iki istasyon arasındaki en hızlı ve en az aktarmalı rotayı bulabilen bir simülasyon geliştirdim ve iki farklı yol bulma algoritması (BFS ve A*) kullanarak bir metro sistemini modelledim.
2.Kullanılan Teknolojiler ve Kütüphaneler
#import collections Bu modül, Python’un standart kütüphanesinde yer alan koleksiyon veri yapılarıyla çalışmamızı sağlar. Örneğin, veri yapılarının düzenli ve hızlı bir şekilde yönetilmesi için çeşitli yardımcı sınıflar içerir.
from collections import defaultdict, deque
defaultdict:
Bu yapı, normal bir sözlük (dict) gibi çalışır fakat bir anahtarın sözlükte bulunmaması durumunda, otomatik olarak belirttiğiniz varsayılan değeri döndürür. Projede, metro hatları gibi gruplandırılmış verileri tutarken, her hat için otomatik olarak boş bir liste oluşturmak için kullanıyorum.
deque:
"Double-ended queue" (iki uçlu kuyruk) anlamına gelir. BFS (Breadth-First Search) algoritmasını uygularken, kuyruk yapısı olarak deque kullanıyorum çünkü deque, eleman ekleme ve çıkarma işlemlerinde listelere göre çok daha verimli çalışıyor.
import heapq
Bu modül, heap veri yapısını (öncelik kuyruğu) oluşturmak ve yönetmek için kullanılır. A* algoritmasında, en kısa sürenin (veya en düşük maliyetin) olduğu yolu seçmek için, heap yapısı sayesinde her seferinde en düşük maliyetli seçeneğe kolayca ulaşabiliyorum.
from typing import Dict, List, Set, Tuple, Optional
Bu modül, Python koduna tip ipuçları (type hints) eklemek için kullanılır. Kodun okunabilirliğini ve bakımını kolaylaştırmak adına Dict: Sözlük yapısını,List: Liste yapısını,Set: Küme yapısını,Tuple: Demet (tuple) yapısını,Optional: Bir değerin olabileceğini ya da olmayabileceğini belirtmek için kullanıyorum.
BFS algoritması (en az aktarmalı rotayı bulmak için) uygulanırken, kuyruk yapısını oluşturmak amacıyla deque kullanırız. deque, listeye göre daha hızlı eleman ekleme ve çıkarma işlemleri sunduğu için genişlik öncelikli arama algoritmalarında tercih ediyoruz.
3. Algoritmaların Çalışma Mantığı 
BFS algoritmasının nasıl çalıştığı:
BFS algoritması, başlangıç noktasından itibaren komşu düğümlerin tümünü keşfederek hedefe ulaşmaya çalışır. Her seviye genişletildiği için, ilk ulaşılan hedef, minimum aktarma (yani minimum düğüm sayısı) ile elde edilir. Projede, collections.deque ile kuyruk yapısı oluşturdum ve ziyaret edilen istasyonlar bir set ile takip edittim.
A* algoritmasının nasıl çalıştığı:
A* algoritması, başlangıç noktasından hedefe giderken, her adımda toplam maliyeti (bu projede süre) minimize etmeye çalışır. heapq kullanılarak oluşturulan öncelik kuyruğu sayesinde, her istasyona ulaşım süresi hesaplanır ve en kısa süreli rota tercih edilir. Ziyaret edilen istasyonlar ve güncellenen süreler, algoritmanın daha verimli çalışmasını sağlar.
Neden bu algoritmaları kullandığımız:
BFS algoritması ile yayılım öncelikli arama yaparız ve ideal çözüme ulaşırız
A* algoritması ile hem en kısa yolu bulmak isterken hem maliyeti de hesaplarız
Örnek Kullanım ve Test Sonuçları:
Projeyi test etmek amacıyla üç temel senaryo üzerinden denemeler yaptım:
AŞTİ'den OSB'ye Rota:
BFS Algoritması: AŞTİ'den başlayarak en az aktarmalı (düğüm sayısı olarak) rota belirlendi.
A Algoritması:* Toplam yolculuk süresi en kısa olacak şekilde hesaplandı.
Batıkent'ten Keçiören'e Rota:
Her iki algoritma da test edildi ve sonuçların tutarlı olduğu görüldü.
Keçiören'den AŞTİ'ye Rota:
Sistem, farklı rota seçeneklerini ve geçişleri doğru şekilde hesaplayarak hem en az aktarmalı hem de en hızlı rotayı sundu.
Testler sırasında, terminal çıktılarından algoritmaların adım adım nasıl çalıştığını da gözlemleyebildim.
Projeyi Geliştirme Fikirleri:
Projenin temel hali böyle oldu ama üzerinde durup revize etmek daha fonksiyonel hale getirmek istiyorum buna görselleştirme eklemek alanı genişletmek kodlarımı düzeltmek ve çok işlevli hale getirmek istiyorum.
