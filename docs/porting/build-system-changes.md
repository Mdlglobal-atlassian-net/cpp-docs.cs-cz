---
title: VCBuild a MSBuild
description: Systém sestavení sady C++ Visual Studio se změnil z vcbuild na MSBuild v aplikaci VIsual Studio 2010.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: afa9324d6074db72fd065cfa07c16349f86a615c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626599"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild a MSBuild: sestavování změn systému v sadě Visual Studio 2010

Systém MSBuild pro C++ projekty byl představen v aplikaci Visual Studio 2010. V aplikaci Visual Studio 2008 a starších verzích byl použit systém VCBuild. Některé typy souborů a koncepty, které jsou závislé na souboru VCBuild, buď neexistují, nebo jsou v nástroji MSBuild jinak reprezentovány. Tento dokument popisuje rozdíly v aktuálním systému sestavení. Chcete-li převést projekt sady Visual Studio 2008 na nástroj MSBuild, je nutné použít Visual Studio 2010. Po převedení projektu byste měli použít nejnovější verzi sady Visual Studio pro upgrade na aktuální prostředí IDE a sadu nástrojů kompilátoru. Další informace, včetně toho, jak získat Visual Studio 2010, najdete v tématu [pokyny pro Visual studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

V následujících částech jsou shrnuty změny z VCBuild na MSBuild. Pokud má projekt vcbuild vlastní pravidla sestavení nebo makra, která nejsou rozpoznána nástrojem MSBuild, přečtěte si téma [projekty sady Visual Studio – Chcete C++ -](../build/creating-and-managing-visual-cpp-projects.md) li zjistit, jak tyto pokyny přeložit do systému MSBuild. Počáteční převod z VCBuild na MSBuild je pouze přechodný krok. Není nutné získat soubor projektu zcela správně nebo získat program pro zkompilování bez chyb. K převedení projektu na formát MSBuild používáte pouze Visual Studio 2010, takže projekt funguje v nejnovější verzi sady Visual Studio.

## <a name="vcproj-is-now-vcxproj"></a>. vcproj je nyní. vcxproj

Soubory projektu již nepoužívají příponu názvu souboru. vcproj. Visual Studio 2010 automaticky převede soubory projektu, které byly vytvořeny ve starší verzi vizuálu C++ , do formátu MSBuild, který používá příponu. vcxproj pro soubory projektu.

## <a name="vsprops-is-now-props"></a>. vsprops je nyní. props

V aplikaci Visual Studio 2008 a starších se *seznamem vlastností projektu* je soubor založený na jazyce XML, který má příponu názvu souboru. vsprops. Seznam vlastností projektu umožňuje zadat přepínače pro nástroje sestavení, jako je například kompilátor nebo linker, a vytvořit uživatelsky definovaná makra. V nástroji MSBuild je přípona názvu souboru pro seznam vlastností projektu. props.

## <a name="custom-build-rules-and-rules-files"></a>Vlastní pravidla sestavení a soubory. Rules

V aplikaci Visual Studio 2008 a starší je *soubor* s pravidly soubor XML, který má příponu názvu souboru. Rules. Soubor pravidel umožňuje definovat vlastní pravidla sestavení a začlenit je do procesu sestavení projektu sady Visual Studio C++ . Vlastní pravidlo sestavení, které může být přidruženo k jedné nebo více příponám názvu souboru, umožňuje předat vstupní soubory nástroji, který vytvoří jeden nebo více výstupních souborů.

V systému MSBuild jsou vlastní pravidla sestavení reprezentovány třemi typy souborů,. XML,. props a. targets namísto souboru. Rules. V případě, že soubor. Rules, který byl vytvořen pomocí dřívější verze C++ vizuálu, je migrován do sady visual Studio 2010, soubory ekvivalent. XML,. props a. targets jsou vytvořeny a uloženy v projektu společně se souborem původní. Rules.

> [!IMPORTANT]
> V aplikaci Visual Studio 2010 rozhraní IDE nepodporuje vytváření nových pravidel. Z tohoto důvodu nejjednodušší způsob, jak použít soubor pravidla z projektu, který byl vytvořen pomocí dřívější verze vizuálu C++ , je migrovat projekt do sady visual Studio 2010.

## <a name="inheritance-macros"></a>Makra dědičnosti

V aplikaci Visual Studio 2008 a dřívější makro **$ (Inherit)** určuje pořadí, ve kterém jsou děděné vlastnosti zobrazeny na příkazovém řádku, který je sestaven systémem sestavení projektu. Makro **$ (Nedědit)** způsobí, že všechny výskyty parametru $ (Inherit) budou ignorovány a způsobí, že všechny vlastnosti, které by jinak byly děděny, nebudou děděny. Například ve výchozím nastavení makro $ (Inherit) způsobí, že se do příkazového řádku připojí možnost kompilátoru [/i (další adresáře include)](../build/reference/i-additional-include-directories.md) .

V aplikaci Visual Studio 2010 je dědění podporováno zadáním hodnoty vlastnosti jako zřetězení jedné nebo více hodnot literálů a maker vlastností. Makra **$ (Inherit)** a **$ (** Inherited) nejsou podporována.

V následujícím příkladu je k vlastnosti na stránce vlastností přiřazena čárkami oddělený seznam. Seznam se skládá ze zřetězení *\<hodnoty >* literálu a hodnoty vlastnosti `MyProperty`, ke kterým se dostanete pomocí zápisu maker **$ (** <em>MyProperty</em> **)** .

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. vcxproj. uživatelské soubory

Uživatelský soubor (. vcxproj. User) ukládá vlastnosti specifické pro uživatele, například nastavení ladění a nasazení. Soubor *vcxproj. User* se vztahuje na všechny projekty pro konkrétního uživatele.

## <a name="vcxprojfilters-file"></a>soubor. vcxproj. filters

Když se **Průzkumník řešení** používá k přidání souboru do projektu, soubor filtrů ( *. vcxproj. filters*) definuje, kde se v zobrazení stromu **Průzkumník řešení** přidá soubor na základě přípony názvu souboru.

## <a name="vc-directories-settings"></a>Nastavení adresářů VC + +

Nastavení C++ vizuálních adresářů je zadáno na [stránce vlastností adresáře VC + +](../ide/vcpp-directories-property-page.md). V aplikaci Visual Studio 2008 a dřívějších nastavení adresáře platí pro jednotlivé uživatele a seznam vyloučených adresářů je zadaný v souboru *sysincl. dat* . 

Pokud spustíte [devenv/ResetSettings](/visualstudio/ide/reference/resetsettings-devenv-exe) na příkazovém řádku, nemůžete změnit nastavení adresáře VC + +. Nemůžete také změnit nastavení, pokud otevřete nabídku **nástroje** , klikněte na **Nastavení importu a exportu**a pak vyberte možnost **resetovat všechna nastavení** .

Migrace nastavení adresářů VC + + ze souboru *. vssettings* , který byl vytvořen starší verzí sady Visual Studio:

1. Otevřete nabídku **nástroje** , klikněte na **Import a export nastavení** .
2. Vyberte možnost **Importovat vybrané nastavení prostředí** .
3. Postupujte podle pokynů v průvodci.

## <a name="see-also"></a>Viz také:

[MSBuild na příkazovém řádku –C++](../build/msbuild-visual-cpp.md)
