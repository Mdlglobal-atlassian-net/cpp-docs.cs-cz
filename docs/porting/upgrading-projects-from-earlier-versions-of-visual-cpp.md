---
title: Upgradování projektů z dřívějších verzí aplikace Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 8848dca10a75bec6f5ff6251a3af5be8e9a7b6e6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816370"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Upgradování projektů z dřívějších verzí aplikace Visual C++

Ve většině případů můžete otevřít projekt, který byl vytvořen v dřívější verzi sady Visual Studio. Je ale nutné projekt v sadě Visual Studio upgradovat. Pokud tento upgradovaný projekt uložíte, nelze ho už pak otevřít v předchozí verzi.

> [!IMPORTANT]
> Pokud se pokusíte převést projekt, který již byl převeden, zobrazí Visual Studio výzvu k potvrzení, protože zpětný převod odstraní existující soubory.

Mnoho upgradovaných projektů a řešení lze úspěšně sestavit bez jakýchkoli úprav. U některých projektů však mohou být nutné změny nastavení, zdrojového kódu nebo obojího. Při řešení potíží s nastavením doporučujeme nejprve postupovat podle následujících pokynů. Pokud se projekt stále nedaří sestavit, pokuste se vyřešit problémy v kódu. Další informace najdete v tématu [přehled potenciálních problémů s upgradem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

1. Vytvořte kopii existujícího projektu a souborů řešení. Nainstalujte aktuální a starší verzi sady Visual Studio paralelně, abyste mohli v případě potřeby porovnávat verze souborů.

2. Otevřete kopii projektu nebo řešení v aktuální verzi sady Visual Studio, tím je upgradujte a poté uložte.

3. U každého převedeného projektu otevřete místní nabídku a zvolte **vlastnosti**. V části **vlastnosti konfigurace**vyberte **Obecné** a potom **sada nástrojů platformy**, vyberte aktuální verzi. (Například pro Visual Studio 2017, vyberte **v141**.)

4. Sestavte řešení. Pokud se sestavení nezdaří, upravte nastavení a spusťte sestavení znovu.

Zdroje dat jsou obsaženy v samostatném databázovém projektu, takže lze snadněji upravovat a ladit procedury, které jsou v nich uloženy. Pokud upgradujete projekt jazyka C++, který obsahuje zdroje dat, automaticky se vytvoří samostatný databázový projekt.

Informace o tom, jak aktualizovat cílová verze Windows najdete v tématu [úpravy WINVER a _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

## <a name="in-this-section"></a>V tomto oddílu

[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Úpravy WINVER a _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Oprava závislostí u interních informací o knihovně](fix-your-dependencies-on-library-internals.md)<br/>
[Problémy migrace s plovoucí desetinnou čárkou](floating-point-migration-issues.md)<br/>
[Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí](use-native-multi-targeting.md)<br/>
[Funkce Visual C++, které jsou ve verzi Preview sady Visual Studio 2019 zastaralé](features-deprecated-in-visual-studio.md)<br/>
[Změny systému sestavení](build-system-changes.md)<br/>

## <a name="see-also"></a>Viz také

[Novinky v jazyce Visual C++ v sadě Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historie změn Visual C++ 2003–2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Nestandardní chování](../cpp/nonstandard-behavior.md)
