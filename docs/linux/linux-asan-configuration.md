---
title: Konfigurace linuxových projektů pro použití sanitizéru adres
description: Popisuje, jak nakonfigurovat projekty C++ Linux v sadě Visual Studio pro použití dezizátoru adresy.
ms.date: 06/07/2019
ms.openlocfilehash: 80e9ab46c948f2062391ae723c3425c435bd4507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364309"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurace linuxových projektů pro použití sanitizéru adres

Ve Visual Studiu 2019 verze 16.1 je podpora AddressSanitizer (ASan) integrovaná do linuxových projektů. ASan můžete povolit pro projekty Linux založené na MSBuild i Projekty CMake. Funguje na vzdálených systémech Linux a na Windows Subsystem pro Linux (WSL).

## <a name="about-asan"></a>O společnosti ASan

ASan je runtime detektor chyb paměti pro C/C++, který zachycuje následující chyby:

- Použít po volném (visící odkaz na ukazatel)
- Přetečení vyrovnávací paměti haldy
- Přetečení vyrovnávací paměti zásobníku
- Použít po návratu
- Použít po oboru
- Chyby inicializačního příkazu

Když ASan zjistí chybu, okamžitě zastaví provádění. Pokud v ladicím programu spustíte program s podporou asan, zobrazí se zpráva popisující typ chyby, adresu paměti a umístění ve zdrojovém souboru, kde k chybě došlo:

   ![Chybová zpráva ASan](media/asan-error.png)

Můžete také zobrazit celý výstup ASan (včetně místa, kde byla přidělena nebo opravena poškozená paměť) v podokně ladění výstupního okna.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Povolení as pro linuxové projekty založené na MSBuild

> [!NOTE]
> Počínaje Visual Studio 2019 verze 16.4, AddressSanitizer pro linuxové projekty je povolena prostřednictvím **konfigurace vlastnosti** > **C/C++** > **Povolit dezinfekci adres**.

Chcete-li povolit as pro linuxové projekty založené na msbuildu, klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **vlastnosti**. Dále přejděte na **vlastnosti** > konfigurace**C/C++** > **Sanitizers**. ASan je povolena prostřednictvím kompilátoru a propojovacího zařízení příznaky a vyžaduje, aby váš projekt překompilován do práce.

![Povolení as pro projekt MSBuild](media/msbuild-asan-prop-page.png)

Volitelné příznaky runtime ASan můžete předat tak, že přejdete na název Konfigurace **Vlastnosti** > **ladění** > **addresssanitizer runtime příznaky**. Kliknutím na šipku dolů přidáte nebo odeberete příznaky.

![Konfigurace příznaků runtime služby ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Povolení projektů ASan pro visual studio CMake

Chcete-li povolit službu ASan pro cmake, klepněte pravým tlačítkem myši na soubor CMakeLists.txt v **Průzkumníku řešení** a zvolte **Nastavení CMake pro Project**.

Ujistěte se, že máte v levém podokně dialogového okna vybranou konfiguraci Linuxu (například **Linux-Debug):**

![Konfigurace ladění Linuxu](media/linux-debug-configuration.png)

Možnosti ASan jsou v části **Obecné**. Zadejte příznaky runtime ASan ve formátu "flag=value", odděleného středníky.

![Konfigurace ladění Linuxu](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Instalace ladicích symbolů ASan

Chcete-li povolit diagnostiku ASan, musíte nainstalovat jeho ladicí symboly (libasan-dbg) na vzdáleném počítači s Linuxem nebo instalaci WSL. Verze libasan-dbg, kterou načtete, závisí na verzi GCC nainstalované na vašem počítači s Linuxem:

|**Verze ASan**|**Verze GCC**|
| --- | --- |
|libasan0 řekl:|gcc-4,8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Pomocí tohoto příkazu můžete určit, kterou verzi GCC máte:

```bash
gcc --version
```

Chcete-li zobrazit verzi libasan-dbg, kterou potřebujete, spusťte program a pak se podívejte na podokno **Ladění** okna **Výstup.** Verze ASan, která je načtena, odpovídá verzi libasan-dbg potřebné na vašem počítači s Linuxem. **Pomocí kláves Ctrl + F** můžete vyhledat "libasan" v okně. Pokud máte například libasan4, zobrazí se řádek jako tento:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Můžete nainstalovat asan ladicí bity na distribucích Linuxu, které používají apt s následujícím příkazem. Tento příkaz nainstaluje verzi 4:

```bash
sudo apt-get install libasan4-dbg
```

Pokud je povolena služba ASan, visual studio vás vyzve v horní části podokna **ladění** **okna Výstup** k instalaci symbolů ladění ASan.
