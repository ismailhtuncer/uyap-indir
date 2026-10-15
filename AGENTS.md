# UYAP Dosya İndirme Aracı — indirme deposu

**Public** repo; yalnız indirme paketlerini (GitHub Releases) ve `README.md`'yi barındırır, kod yoktur.
Kaynak kod private `ismailhtuncer/uyap-araci`'dedir. Release'leri oranın CI'si (`.github/workflows/build.yml`, elle çalıştırılır)
`build-<n>` etiketiyle önce taslak olarak oluşturur, paketleri yükleyip yayınlar. Derleme/test komutu bu repoda yoktur.

## Release'ler ve otomatik güncelleme

- Uygulamanın güncelleyicisi (`uyap-araci/uyap/guncelleme.py`) bu reponun releases API'sini token'sız okur; listeyi en yeniden geriye
  tarar ve kendi platform varlığını içeren ilk release'i seçer.
- Varlık adları sabittir: `UYAP-macOS.dmg`, `UYAP-macOS.zip` (otomatik güncelleme), `UYAP-Windows.zip`, `SHA256SUMS`,
  `SHA256SUMS.sig` (Ed25519 imzası). Adlar değiştirilmez; imzası uymayan paketi uygulama kurmaz.
- Release oluşturmak, yayınlamak, düzenlemek, silmek, varlık yüklemek/değiştirmek ya da "latest"i değiştirmek yalnız kullanıcı açıkça
  isteyince yapılır; normalde bunu yalnız uyap-araci CI'si yapar (o da yalnız kullanıcı "push et ve yayınla" deyince başlatılır).
- Etiket biçimi `build-<n>`; güncelleyici yalnız bilinen etiket biçimlerini kabul eder.
- Release notları Türkçe ve kullanıcıya (avukata) yöneliktir.

## Dal ve PR

- `main`'e doğrudan push yok. Dal koruması kapalı; bu kural yalnız burada yazılıdır, uy.
- Her iş kendi dalında (`docs/...`, `fix/...`); PR tabanı `main`.
- Bulut Claude oturumları değişikliği yazar ve PR açar; PR'ı kullanıcının yerel oturumu inceler ve birleştirir. PR'ı kendin birleştirme.
- Commit ve PR metinleri kısa Türkçe. Commit'e `Co-Authored-By: Claude` satırı, PR açıklamasına "Generated with Claude Code" satırı eklenmez.

## Kurallar

- Repo herkese açıktır: kaynak kod, gizli bilgi (token, imza anahtarı), müvekkil verisi ya da kişisel UYAP/UETS bilgisi buraya konmaz.
- `README.md` indirme talimatıdır; kısa ve kullanıcıya yönelik kalır.
