Bu depo, Siemens TIA Portal yazılımı kullanılarak geliştirilmiş, farklı endüstriyel otomasyon senaryolarını içeren bir dizi bağımsız projeyi bir araya getirmektedir. Her bir proje, motorlar, fanlar ve kompresörler gibi ekipmanların kontrolünü ve durum izlemesini göstermektedir. Projeler, temel PLC programlama mantıklarını (start/stop lojiği, SR ve RS blokları) ve HMI arayüzlerinin bu sistemleri nasıl yönetmek için kullanıldığını anlamak için ideal bir koleksiyondur.

Çalışma Mantığı
Bu gruptaki projeler, her biri farklı bir amaca hizmet eden birden fazla bağımsız senaryoyu kapsar. Çalışma mantıkları aşağıda her bir senaryo için ayrı ayrı açıklanmıştır.

1. Tek Butonla Start/Stop Kontrolü (Kenar Tetikleme)
Bu senaryo, tek bir butonu kullanarak bir motoru veya fanı başlatma ve durdurma mantığını gösterir.

Lojik: %I0.0 (StartStop) girişi, hem pozitif kenar (P_TRIG) hem de negatif kenar (N_TRIG) tetiklemeleri ile kontrol edilir.

P_TRIG (Pozitif Kenar): Butona basıldığında (kapalıdan açıka geçtiğinde) P_TRIG aktif olur. Bu, SR (Set-Reset) bloğunun S girişini tetikler ve motoru çalıştırır.

N_TRIG (Negatif Kenar): Buton bırakıldığında (açıktan kapalıya geçtiğinde) N_TRIG aktif olur. Bu, SR bloğunun R1 girişini tetikler ve motoru durdurur.

Çıkışlar: Bu lojik, %Q4.0 (Fan) ve %Q4.1 (Motor) gibi çıkışları kontrol eder.

2. Mandallamalı (Latched) ve Anlık (Momentary) Buton Kontrolü
Bu senaryo, HMI'da farklı buton tiplerinin nasıl kullanıldığını gösterir.

Mandallamalı (LATCHED) Buton: HMI'da %I0.0'a bağlı LATCHED butonu, basıldığında durumunu korur. PLC'deki SR bloğunun S girişini aktif ederek %Q4.0 (Motor) çıkışını kalıcı olarak SET eder.

Anlık (MOMENTARY) Buton: HMI'da %I0.1'e bağlı MOMENTARY butonu, sadece basılı tutulduğu sürece aktif kalır. Bu, SR lojiğiyle birleşik olarak motorun çalışması için bir koşul sağlayabilir.

Durdurma (STOP) Butonu: %I0.2'ye bağlı STOP butonu, SR bloğunun R1 girişini tetikleyerek %Q4.0 (Motor) çıkışını RESET eder ve motoru durdurur.

3. Motor ve Kompresör Kontrolü Uygulaması
Bu senaryo, bir fan, bir motor ve bir kompresörden oluşan bir sistemin HMI arayüzü ile nasıl kontrol edildiğini gösterir.

Görselleştirme: HMI ekranında, bir FAN (%Q4.0), bir MOTOR (%Q4.1) ve bir COMPRESSOR sembolleri yer alır.

Kontrol: Ekranın altındaki START / STOP butonu (%I0.0), tek bir noktadan hem fan hem de motoru kontrol eder. Bu buton, bir önceki senaryodaki gibi kenar tetikleme lojiği ile programlanmıştır.

İşlev: Butona basıldığında fan ve motor çalışır, tekrar basıldığında ise durur. Kompresör muhtemelen bu motor veya fanın çalışmasına bağlı olarak otomatik olarak devreye girer.
