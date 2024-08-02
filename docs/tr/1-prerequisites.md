# Node.js Çalıştayı - Hazırlık

## Araçlar

- [Node.js Çalıştayı - Hazırlık](#nodejs-çalıştayı---hazırlık)
  - [Araçlar](#araçlar)
    - [Geliştirme Ortamı](#geliştirme-ortamı)
    - [Node.js \& package manager](#nodejs--package-manager)
    - [Veri Taban(lar)ı](#veri-tabanları)
    - [Başka?](#başka)
  - [Sonraki Adım](#sonraki-adım)

### Geliştirme Ortamı

- [Visual Studio Code](https://code.visualstudio.com/) bu çalıştay için varsayılan editörümüz ve mikro IDE olacaktır. Ancak, alışkanlıklarınıza göre mevcut ortamınızla da devam edebilirsiniz: [NetBeans](https://netbeans.apache.org/front/main/index.html), [Emacs](https://www.gnu.org/software/emacs/download.html), [WebStorm](https://www.jetbrains.com/webstorm/). Hatta Vi, nano veya işletim sisteminiz ile gelen notepad bile.

- [Visual Studio Code](https://code.visualstudio.com/) yüklediyseniz, bu çalıştay kapsamında aşağıdaki eklentiler işinizi kolaylaştıracaktır:
  - [ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
  - [mgmcdermott.vscode-language-babel](https://marketplace.visualstudio.com/items?itemName=mgmcdermott.vscode-language-babel)
  - [ldd-vs-code.better-package-json](https://marketplace.visualstudio.com/items?itemName=ldd-vs-code.better-package-json)
  - [esbenp.prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  - [christian-kohler.path-intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
  - [christian-kohler.npm-intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
  - [Angular.ng-template](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
  - [cyrilletuzi.angular-schematics](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.angular-schematics)

### Node.js & package manager

```Node.js``` bir JavaScript çalıştırma ortamı, bu çalıştay için en ana araç görevi görecek. ```npm``` olarak bilinen paket yönetici ise beraberinde gelir.

[Buradan](https://nodejs.org/en/download/prebuilt-installer) işletim sisteminiz için uygun olan bir Node.js yükleyicisi kullanabilirsiniz. Bu npm'i de kurar. Mevcüt LTS versiyonu indirebilirsiniz. Yükleyicide sunulan ek içeriği (örn. Chocolatey) kurmanıza gerek yok. Yükleme sonrası işlemin başarılı olduğundan emin olmak üzere terminalinize girin. İşlem başarılıysa:

- ```node -v``` komutu ```v20.10.0``` (yüklenen Node.js sürümünün SemVer gösterimi ) gibi bir çıktı vermeli
- ```npm -v``` komutu dahi benzer bir çıktı verir; örn. ```10.6.0```

Artık sonraki araca devam edebiliriz.

### Veri Taban(lar)ı

- [PostgreSQL](https://www.postgresql.org/download/) başlıca veri tabanı sistemimiz olacaktır. Yerel ortamınızda kurulumu önerilir. Node.js için olduğu gibi, bunun için de hazır yükleyici kullanılabilir, [buradan indirebilirsiniz.](https://www.postgresql.org/download/).
- [REDIS](https://redis.io/) bazı örneklerde kullanılacak. MacOS veya linux kullanıcısı iseniz, kurulumu basittir; ancak Windows için [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) gerekir. Kurulumunu kendi başınıza yapamazsanız mentorünüzden yardım isteyin.

### Başka?

Bir de tarayıcıya ihtiyacınız olacak ki, bilgisayarınızda mevcüttür. Herhangi bir modern tarayıcı iş görür.

## Sonraki Adım
