---
title: Konfigurace linuxových projektů pro použití sanitizéru adres
description: Popisuje, jak nakonfigurovat C++ projekty pro Linux v aplikaci Visual Studio na používání programu pro úpravu adres.
ms.date: 06/07/2019
ms.openlocfilehash: da7197981a431becfc1231dae96f7542062de675
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195855"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurace linuxových projektů pro použití sanitizéru adres

V aplikaci Visual Studio 2019 verze 16,1 je podpora AddressSanitizer (ASan) integrovaná do projektů Linux. ASan můžete povolit pro projekty Linux založené na MSBuild i pro projekty CMake. Funguje na vzdálených systémech Linux a v subsystému Windows pro Linux (WSL).

## <a name="about-asan"></a>O ASan

ASan je detektor chyb běhové paměti pro C/C++ , který zachycuje následující chyby:

- Použít po uvolnění (odkaz na ukazatel dangling)
- Přetečení vyrovnávací paměti haldy
- Přetečení vyrovnávací paměti zásobníku
- Použít po návratu
- Použít po oboru
- Chyby pořadí inicializace

Když ASan detekuje chybu, zastaví se okamžitě. Pokud v ladicím programu spustíte program s podporou ASan, zobrazí se zpráva, která popisuje typ chyby, adresu paměti a umístění ve zdrojovém souboru, kde došlo k chybě:

   ![Chybová zpráva ASan](media/asan-error.png)

Můžete také zobrazit úplný výstup ASan (včetně místa, kde byla poškozená paměť přidělena nebo vrácena) v podokně ladění okna výstup.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Povolit ASan pro projekty Linux založené na MSBuildu

> [!NOTE]
> Od verze Visual Studio 2019 verze 16,4 jsou AddressSanitizer pro projekty pro Linux povolené prostřednictvím **vlastností** > konfigurace**C/C++**  > **Povolit úpravu adres**.

Pokud chcete povolit ASan pro projekty Linux založené na MSBuild, klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **vlastnosti**. Potom přejděte do **vlastností** > konfigurace**C/C++**  > oddálení. ASan je povoleno prostřednictvím příznaků kompilátoru a linkeru a vyžaduje, aby byl projekt znovu zkompilován, aby fungoval.

![Povolení ASan pro projekt MSBuild](media/msbuild-asan-prop-page.png)

Volitelné příznaky modulu runtime ASan můžete předat tak, že přejdete na **vlastnosti** > konfigurace**ladění** > **příznaků modulu runtime AddressSanitizer**. Kliknutím na šipku dolů přidejte nebo odeberte příznaky.

![Konfigurace příznaků modulu runtime ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Povolit ASan pro projekty sady Visual Studio CMake

Pokud chcete povolit ASan pro CMake, klikněte pravým tlačítkem myši na soubor CMakeLists. txt v **Průzkumník řešení** a vyberte **Nastavení cmake pro projekt**.

Ujistěte se, že v levém podokně dialogového okna máte zvolenou konfiguraci pro Linux (například **Linux-Debug**):

![Konfigurace ladění pro Linux](media/linux-debug-configuration.png)

Možnosti ASan jsou **obecně**. Zadejte příznaky modulu runtime ASan ve formátu "příznak = hodnota", které jsou odděleny středníky.

![Konfigurace ladění pro Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Nainstalovat symboly ladění ASan

Pokud chcete povolit diagnostiku ASan, musíte na svém vzdáleném počítači se systémem Linux nebo instalaci WSL nainstalovat symboly pro ladění (libasan-DBG). Verze libasan-DBG, kterou načtete, závisí na verzi aplikace RSZ nainstalované na počítači se systémem Linux:

|**Verze ASan**|**Verze RSZ**|
| --- | --- |
|libasan0|RSZ – 4,8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Pomocí tohoto příkazu můžete určit, kterou verzi RSZ máte:

```bash
gcc --version
```

Chcete-li zobrazit verzi libasan-DBG, kterou potřebujete, spusťte program a podívejte se na podokno **ladění** v okně **výstup** . Nahraná verze ASan odpovídá verzi libasan-DBG potřebné na počítači se systémem Linux. Pomocí **kombinace kláves CTRL + F** můžete v okně Vyhledat text "libasan". Pokud jste libasan4 například, zobrazí se řádek podobný tomuto:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

ASan ladění můžete nainstalovat na Linux distribuce, které používají APT, pomocí následujícího příkazu. Tento příkaz nainstaluje verzi 4:

```bash
sudo apt-get install libasan4-dbg
```

Pokud je povolený ASan, Visual Studio vás vyzve v horní části podokna **ladění** okna **výstup** , aby se nainstalovaly symboly ladění ASan.
