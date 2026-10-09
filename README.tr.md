# Tanıtım Zamanlayıcısı

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Mezunlar buluşması gibi etkinliklerde herkesin sırayla kendini tanıtması için tek sayfalık bir zamanlayıcı. `index.html` dosyasını tarayıcıda açmanız yeterli — kurulum, sunucu veya internet bağlantısı gerekmez.

## Kullanım

1. `index.html` dosyasını tarayıcıda açın (Safari / Chrome).
2. Ayarlar ekranında: CSV yükleyin (`sample/participants.csv` dosyasına bakın veya “Örnek yükle”yi kullanın), kişilerin katılım durumunu değiştirin, istediğiniz alana göre sıralayın, başlık / kişi başı süre / hitap / dili ayarlayın ve sesleri deneyin.
3. “Zamanlayıcıya git”e basın (bu, sesi de etkinleştirir).
4. Zamanlayıcıyı yönetin:

| Eylem | Etki |
|---|---|
| `Boşluk` / Başlat düğmesi | Sıradaki kişiyi başlatır (alkışla) |
| Sağdaki listede bir isme tıklama | O kişiyi başlatır; öncesindekiler “Atlananlar”a geçer |
| “Atlananlar”daki bir isme tıklama | O kişiyi başlatır |
| “Atlananlar”da “Katılıyor” işaretini kaldırma | Onaydan sonra yok sayılır ve listeden çıkarılır (zamanlayıcı durmaz) |

Son 10 sn: her saniye tik sesi · son 3 sn: hızlı bip sesleri · 0 sn: patlama sesi ve “Süre doldu!” etiketi. Sağ üstte toplam geçen süre, sağ sütunda sonraki 10 kişi görünür.

## CSV biçimi

İlk satır başlık satırıdır. UTF-8 ve Shift_JIS otomatik algılanır. İsim ve hitap sütunları başlıktan (ör. `isim`, `hitap`) otomatik seçilir ve ayarlardan değiştirilebilir. Hitap hücresi boşsa varsayılan hitap kullanılır.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Diller

16 dil: Ayarlar ekranındaki “Dil”den değiştirin (başta tarayıcı dili kullanılır, seçiminiz kaydedilir). Arayüz metinleri, varsayılan başlık ve hitap, örnek veriler ve hitabın konumu (ismin önünde/ardında) dile göre değişir; Arapçada sağdan sola yerleşim kullanılır. Çeviriler ana dili konuşanlarca denetlenmedi — düzeltmek için `index.html` içindeki `I18N` bölümünü düzenleyin. Dil eklemek için `LANGS`, `I18N` ve `SAMPLE_NAMES` içine birer kayıt ekleyin.

## Mobil

Telefonlar için dikey ve yatay yerleşimler vardır. iPhone’da sessiz anahtarı açıksa ses çıkmaz. Dosyayı “Dosyalar” uygulamasından açmak en güvenilir yoldur; GitHub Pages ile yayınlarsanız bir URL’yi açmanız yeterlidir.

## Yapı

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` her şeyi içerir: dil sözlüğü, CSV ayrıştırıcı, ayarlar ekranı, Web Audio ile ses sentezi (ses dosyası yok), zamanlayıcı mantığı (zaman damgasına dayalı, kayma yapmaz) ve çalışma ekranı. Ayarlar ve ilerleme otomatik olarak `localStorage`’a kaydedilir.

Lisans: [MIT](LICENSE)
