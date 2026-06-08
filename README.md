# GitHub Actions CI/CD Deployment Workflow

Bu proje, modern yazılım geliştirme süreçlerinin kalbi olan Sürekli Entegrasyon ve Sürekli Dağıtım (CI/CD) kavramlarını uygulamak amacıyla geliştirilmiştir. Proje kapsamında, `index.html` dosyasında yapılan her değişiklik GitHub Actions iş akışı (workflow) tarafından otomatik olarak yakalanır ve insan müdahalesi olmadan doğrudan GitHub Pages üzerinde canlıya alınır.

## Proje Mimarisi ve Klasör Yapısı

Otomasyonun (GitHub Actions) tetiklenebilmesi için proje şu standart yapıya göre kurgulanmıştır:

    gh-deployment-workflow/
    ├── .github/
    │   └── workflows/
    │       └── deploy.yml      # CI/CD Otomasyon (Workflow) Dosyası
    ├── index.html              # Canlıya Alınan Web Sitesi
    └── README.md               # Proje Dokümantasyonu

## CI/CD İş Akışı Nasıl Çalışır?

1. Geliştirici yerel bilgisayarında `index.html` dosyasını günceller ve `main` branch'ine pushlar.
2. `deploy.yml` içerisindeki `paths` filtresi sayesinde, sadece `index.html` değiştiğinde tetiklenecek bir tetikleyici (webhook) devreye girer.
3. GitHub Actions, bulutta temiz bir Ubuntu sunucusu ayağa kaldırır.
4. Kodlar sunucuya çekilir, güvenlik izinleri doğrulanır, paketlenir ve GitHub Pages sunucularına otomatik olarak aktarılır (Continuous Deployment).

## Canlı Önizleme

Eğer tüm adımlar başarıyla tamamlandıysa, web sitesine aşağıdaki URL formatından dünya çapında erişilebilir:

    https://<github-kullanici-adiniz>.github.io/gh-deployment-workflow/

## Kazanımlar

Bu çalışma ile; YAML formatında iş akışı (workflow) yazımı, event-driven (olaya dayalı) tetikleyiciler, bulut runner mimarisi, RBAC (rol tabanlı erişim kontrolü) izinlerinin tanımlanması ve statik web sitelerinin otomatik dağıtım süreçleri pratik edilmiştir.