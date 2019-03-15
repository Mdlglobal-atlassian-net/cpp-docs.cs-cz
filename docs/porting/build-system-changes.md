---
title: Sestavení systému změny v sadě Visual Studio 2010
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823457"
---
# <a name="build-system-changes"></a>Změny systému sestavení

Systém MSBuild se používá k sestavení projektů Visual C++. V sadě Visual Studio 2008 a dřívějších verzích, ale systém VCBuild se použil. Některé typy souborů a koncepty, které závisí na VCBuild neexistují nebo jsou reprezentovány odlišně v aktuálním systému. Tento dokument popisuje rozdíly v aktuálním systému sestavení.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj je nyní .vcxproj

Soubory projektu již nebudete používat .vcproj příponu názvu souboru. Visual Studio automaticky převádí soubory projektu, které byly vytvořeny pomocí starší verze jazyka Visual C++ do formátu, který se používá v aktuálním systému. Další informace o tom, jak ručně upgradovat projekt, naleznete v tématu [/upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

V aktuální verzi přípona názvu souboru pro soubor projektu je VCXPROJ.

## <a name="vsprops-is-now-props"></a>.vsprops je nyní .props

V dřívějších verzích *seznam vlastností projektu* je soubor založený na formátu XML, který má příponu názvu souboru .vsprops. Seznam vlastností projektu umožňuje zadat parametry pro sestavení nástrojů, jako je kompilátoru nebo linkeru a vytvořit uživatelská makra.

Přípona názvu souboru pro seznam vlastností projektu v aktuální verzi je .props.

## <a name="custom-build-rules-and-rules-files"></a>Vlastní sestavení pravidel a .rules soubory

V dřívějších verzích *soubor pravidel* je soubor založený na formátu XML, který má příponu názvu souboru .rules. Soubor pravidel umožňuje definovat vlastní pravidla sestavení a začlenit do procesu sestavení projektu ve Visual C++. Pravidlo vlastního sestavení, které může být přidružený jeden nebo více přípon souborů, umožňuje předání vstupních souborů do nástrojů, která obsahuje jeden nebo více výstupních souborů.

V této verzi pravidla vlastního sestavení jsou reprezentovány tři typy souborů, XML, .props a .targets, nikoli soubor .rules. Při migraci .rules souboru, který byl vytvořen pomocí dřívější verze aplikace Visual C++ na aktuální verzi, ekvivalentní soubory .xml, .props a .targets jsou vytvořeny a uloženy ve vašem projektu společně s původní soubor .rules.

> [!IMPORTANT]
>  V aktuální verzi rozhraní IDE nepodporuje vytváření nových pravidel. Z tohoto důvodu je nejjednodušší způsob, jak použít soubor pravidlo z projektu, který byl vytvořen pomocí dřívější verze aplikace Visual C++ chcete projekt migrovat, na aktuální verzi.

## <a name="inheritance-macros"></a>Makra dědičnosti

V dřívějších verzích **$(Inherit)** – makro určuje pořadí zděděné vlastnosti na příkazovém řádku, který se skládá ze sestavení systém projektu. **$(NoInherit)** – makro způsobí, že všechny výskyty $(Inherit) ignorovat a způsobí, že všechny vlastnosti, které by jinak se dědí, není odvozeny. Například ve výchozím nastavení $(Inherit) – makro způsobí, že soubory určené vlastností [/I (další vložené adresáře)](../build/reference/i-additional-include-directories.md) – možnost kompilátoru připojit k příkazovému řádku.

V aktuální verzi je podporována dědičnost tak, že zadáte hodnotu vlastnosti jako zřetězení jeden nebo více literálních hodnot a makra vlastností. **$(Inherit)** a **$(NoInherit)** makra nejsou podporovány.

V následujícím příkladu je seznam oddělený středníkem přiřazená vlastnost na stránce vlastností. Seznam obsahuje zřetězení  *\<hodnota >* literál a hodnota `MyProperty` vlastnost, která je přístupné pomocí zápisu – makro, **$(**  <em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. vcxproj.user soubory

Uživatelský soubor (. vcxproj.user) ukládá vlastnosti specifické pro uživatele, pro příklad, ladění a nasazení nastavení. Soubor vcxproj.user platí pro všechny projekty pro určitého uživatele.

## <a name="vcxprojfilters-file"></a>. vcxproj.filters souboru

Když **Průzkumníku řešení** se používá k přidání souboru do projektu soubor filtrů (. vcxproj.filters) definuje, v které **Průzkumníka řešení** stromovém zobrazení se přidá soubor, na základě jeho přípony názvu souboru.

## <a name="vc-directories-settings"></a>Nastavení adresáře VC ++

Nastavení adresáře Visual C++ jsou určeny na [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md). V dřívějších verzích sady Visual Studio nastavení adresáře se vztahují na uživatele a seznam vyloučených adresářů je uveden v souboru sysincl.dat.

Nastavení adresáře VC ++ nejde změnit, pokud spustíte [devenv/resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) na příkazovém řádku. Můžete také nemůžete měnit nastavení, pokud otevřete **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**a pak vyberte **obnovit všechna nastavení** možnost.

Migrace nastavení adresáře VC ++ ze souboru .vssettings, který je vytvořen pomocí dřívější verze aplikace Visual C++. Otevřít **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**vyberte **importovat vybrané nastavení prostředí**a pak postupujte podle pokynů v průvodci. Nebo když spustíte Visual Studio poprvé, na **zvolte výchozí nastavení prostředí** dialogu **migrovat nastavení oprávnění z předchozí verze a použít je kromě výchozího nastavení vybrané níže**.

## <a name="see-also"></a>Viz také:

[MSBuild na příkazovém řádku - C++](../build/msbuild-visual-cpp.md)
