---
title: Konfigurace projektů Linux použít adresu Sanitizer
description: Popisuje postup konfigurace C++ Linuxové projekty v sadě Visual Studio používat Sanitizer adresu.
ms.date: 06/07/2019
ms.openlocfilehash: 2415e8971614de35f046b699ce99c3822faf9372
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66823570"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurace projektů Linux použít adresu Sanitizer

V aplikaci Visual Studio 2019 verze 16.1 podporu AddressSanitizer (ASan) je integrovaná do Linuxové projekty. ASan můžete povolit pro projekty CMake a založené na MSBuild Linuxové projekty. Funguje na vzdálených Linuxových systémů a v subsystému Windows pro Linux (WSL).

## <a name="about-asan"></a>O ASan

ASan je chyba detektoru paměti s modulu runtime pro C /C++ , který zachytí následující chyby:

- Použít po free (nepropojená ukazatel odkaz)
- Přetečení vyrovnávací paměti haldy
- Přetečení vyrovnávací paměti zásobníku
- Použít po návratu
- Použít po oboru
- Inicializace pořadí chyb

Když ASan zjistí chybu, zastaví provádění okamžitě. Při spuštění aplikace ASan povolené v ladicím programu, zobrazí se zpráva, která popisuje typ chyby, adresa paměti a umístění ve zdrojovém souboru, kde došlo k chybě:

   ![ASan chybová zpráva](media/asan-error.png)

Můžete také zobrazit úplný výstup ASan (včetně, kde je poškozená paměť byla přidělena/navrácena) v podokně ladění okna výstup.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Povolení ASan pro projekty založené na MSBuild Linux

Povolení ASan pro projekty založené na MSBuild Linux, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti**. Dále přejděte do **vlastnosti konfigurace** > **C /C++**  > **Sanitizers**. ASan povolená přes kompilátoru a příznaky linkeru a vyžaduje projekt tak, aby překompilují. pro práci.

![Povolit ASan pro projekt MSBuild](media/msbuild-asan-prop-page.png)

Volitelné příznaky ASan runtime můžete předat tak, že přejdete do **vlastnosti konfigurace** > **ladění** > **AddressSanitizer Runtime příznaky**. Klikněte na šipku dolů a přidat nebo odebrat příznaky.

![Konfigurace modulu runtime příznaky ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Povolení ASan pro projekty Visual Studio CMake

Povolit ASan pro CMake, klikněte pravým tlačítkem na soubor CMakeLists.txt v **Průzkumníka řešení** a zvolte **nastavení CMake pro projekt**.

Ujistěte se, že máte Linux konfiguraci (například **Linux ladění**) vybraný v levém podokně dialogového okna:

![Konfigurace ladění systému Linux](media/linux-debug-configuration.png)

Možnosti ASan jsou v rámci **Obecné**. Zadat příznaky runtime ASan ve formátu "Příznak = Hodnota", oddělené středníky.

![Konfigurace ladění systému Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Nainstalujte ASan symboly ladění

Povolit diagnostiku ASan, je nutné nainstalovat jeho symboly ladění (libasan dbg) na vzdáleném počítači s Linuxem nebo WSL instalace. Verze libasan dbg, který načtete závisí na verzi GCC nainstalovat na počítač s Linuxem:

|**ASan version**|**Verze GCC**|
| --- | --- |
|libasan0|gcc 4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Můžete určit, kterou verzi GCC získáte pomocí tohoto příkazu:

```bash
gcc --version
```

Pokud chcete zobrazit verzi libasan dbg, je třeba, spusťte program a podívejte se na **ladění** podokně **výstup** okna. Verze ASan, který je načten odpovídá verzi libasan-dbg potřeba na počítač s Linuxem. Můžete použít **Ctrl + F** "libasan" v okně hledání. Pokud máte libasan4, například se zobrazí řádek podobný následujícímu:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Služba bits ASan ladění můžete nainstalovat na distribucí Linuxu, které pomocí apt pomocí následujícího příkazu. Tento příkaz nainstaluje verzi 4:

```bash
sudo apt-get install libasan4-dbg
```

Pokud je povolené ASan, Visual Studio vás vyzve k horní části **ladění** podokně **výstup** okna nainstalujte ASan symboly ladění.
