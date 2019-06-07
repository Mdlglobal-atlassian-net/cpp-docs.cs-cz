---
title: Upravit a Refaktorovat C++ kódu v sadě Visual Studio
description: Použití C++ editoru kódu v sadě Visual Studio k formátování, navigace, pochopit a Refaktorovat kód.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: d4a74608a95df0fdd461f55d26fee97332a66aa8
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741620"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Upravit a Refaktorovat C++ kódu v sadě Visual Studio

Visual Studio poskytuje několik nástrojů, které vám pomohou vytvořit, upravit a Refaktorovat kód.

##  <a name="intellisense"></a>IntelliSense

Technologie IntelliSense je výkonný dokončení nástroj kódu, která během psaní navrhuje symboly a fragmenty kódu za vás. C++Technologie IntelliSense v sadě Visual Studio spustí v reálném čase, analýzu vašeho základu kódu při aktualizaci a poskytuje doporučení. Při psaní více znaků, seznam doporučených výsledky zúžit.

![C&#43; &#43; rozevíracího seznamu člena seznamu](../ide/media/cpp-statement-completion.png)

Některé symboly jsou vynechány automaticky abychom výsledky upřesněte. Například při přístupu k objektu třídy členů mimo třídu, nebudete moci zobrazit soukromé členy ve výchozím nastavení nebo chráněné členy (Pokud nejste v kontextu podřízené třídy) položku. Můžete nastavit filtrování pomocí tlačítek v dolní části.

Až výběrem symbolu z rozevíracího seznamu, můžete provést automatické dokončování s **kartu**, **Enter**, nebo jednu z dalších znaků potvrzení změn (ve výchozím nastavení: {} [ ](). ,:, +-* / % & | ^! =? @#\). Přidání nebo odebrání znaků z tohoto seznamu, vyhledávání "IntelliSense" v **Snadné spuštění** (Ctrl + Q) a zvolte **textový Editor > C /C++ > Upřesnit** možnost. **Znaků potvrzení seznamu členů** možnost umožňuje přizpůsobení seznamu s požadované změny.

**Režim filtrování seznamu členů** možnost řídí, jaké druhy návrhy automatického dokončování IntelliSense zobrazí. Ve výchozím nastavení, je nastavit **Fuzzy**. V přibližné vyhledávání, pokud máte symbol volá *MyAwesomeClass*, můžete zadat "MAC" a najít třídu ve své návrhy automatického dokončování. Algoritmu přibližné Nastaví minimální prahovou hodnotu, která se zobrazí v seznamu musí splňovat symboly. **Inteligentní** filtrování zobrazí všechny symboly obsahující podřetězce, které odpovídají jste zadali. **Předpona** filtrování hledá řetězce, které začínají jste zadali.

Další informace o C++ technologie IntelliSense, najdete v článku [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) a [konfigurovat C++ projekt tak, aby IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

IntelliCode je technologie IntelliSense s asistencí AI. Uloží je pravděpodobně Release candidate v horní části seznamu dokončení. Doporučení IntelliCode jsou založená na tisíce open source projektů na Githubu každý s více než 100 hvězdiček. V kombinaci s kontextem vašeho kódu, je seznam pro doplňování přizpůsobená pro podporu běžné postupy.

Při zápisu C++, IntelliCode vám pomůže při používání oblíbených knihoven, jako C++ standardní knihovny. Kontext kódu slouží k poskytování doporučení nejužitečnější nejprve. V následujícím příkladu `size` členská funkce se často používá u `sort` fungovat, takže se zobrazí na začátek seznamu výsledků.

![C&#43; &#43; IntelliCode](../ide/media/intellicode-cpp.png " C++ IntelliCode")

::: moniker range="vs-2019"

Visual Studio 2019 IntelliCode je dostupné jako volitelná součást v  **C++ Desktop Development** pracovního vytížení. Abyste měli jistotu, že je aktivní pro IntelliCode C++, přejděte na stránku **nástroje** > **možnosti** > **IntelliCode**  >  **Obecné** a nastavte  **C++ základní model** k **povoleno**.

::: moniker-end

::: moniker range="vs-2017"

V sadě Visual Studio 2017 IntelliCode je dostupný jako rozšíření Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Prediktivní IntelliSense (experimentální)

**Prediktivní IntelliSense** je experimentální funkce, která používá kontextové sledování lze omezit výsledky zobrazené v rozevíracím seznamu technologie IntelliSense. Algoritmus použije typ odpovídající tak, aby se zobrazuje jenom výsledky, které odpovídají očekávanému typu. V nejjednodušším případě, pokud zadáte `int x =` a vyvolání rozevíracího seznamu technologie IntelliSense, zobrazí se jen celá čísla nebo funkce vrací celá čísla. Tato funkce je vypnuto ve výchozím nastavení protože je stále ve vývoji. Funguje nejlépe s globální symboly; Členské funkce zatím nepodporují. Můžete zapnout ho tak, že zadáte "Prediktivní" **Snadné spuštění** nebo tak, že přejdete do **nástroje** > **možnosti** > **textový Editor**  >  **C /C++**  > **experimentální** > **povolit prediktivní IntelliSense**.

Chcete-li přepsat **prediktivní IntelliSense** a zobrazit je delší seznam, stiskněte klávesu **Ctrl + J**. Pokud **prediktivní IntelliSense** zapnutý, vyvolání **Ctrl + J** odebere prediktivní filtr. Stisknutím klávesy **Ctrl + J** znovu odebere výsledků usnadnění filtr ze seznamu členů podle potřeby. Tlačítko na ([+]) v rámci technologie IntelliSense rozevíracího seznamu udělá to stejné jako **Ctrl + J**. Najeďte myší na tlačítko Zobrazit popis informací o co se zobrazuje.

![C&#43; &#43; prediktivní IntelliSense](../ide/media/predictive-intellisense-cpp.png "prediktivní IntelliSense")

Na předchozím snímku obrazovky ukazuje několik tlačítek v rozevíracím seznamu. Povolit tyto filtry IntelliSense pro různé druhy výsledky:

- Proměnné a konstanty
- Funkce
- Typy
- Makra
- Výčty
- Jmenné prostory

Tlačítko se zobrazí pouze v případě, že je relevantní pro aktuální relaci IntelliSense. Obvykle se nezobrazí všechna tlačítka ve stejnou dobu.

## <a name="template-intellisense"></a>Šablona IntelliSense

Když blikající kurzor se nachází uvnitř definice šablony, **šablony panelu** se zobrazí, což vám umožní zadat argumenty šablony vzorku pro technologii IntelliSense. 

![C&#43; &#43; instance existujících šablon technologie IntelliSense zobrazovat](../ide/media/template-intellisense-cpp-1.png "instance existujících šablon technologie IntelliSense Show")

Klikněte na tlačítko **<T>** ikonu pro rozbalení/sbalení **šablony panel**. Klikněte na ikonu tužky nebo dvakrát klikněte **šablony panel** otevřete **upravit** okno. 

![C&#43; &#43; šablony IntelliSense](../ide/media/template-intellisense-cpp-3.png "šablony IntelliSense")

Úpravy, které provedete v okně se použijí přímo do zdrojového kódu, takže uvidíte účinky v reálném čase. 

Na panelu šablony lze automaticky vyplnit pole kandidátů podle instancí ve vašem kódu. Klikněte na **přidat všechny existující instancí** zobrazíte seznam všech konkrétní argumentů, které se používají k vytvoření instance šablony v rámci vašeho základu kódu.

![C&#43; &#43; seznamu výsledků šablony IntelliSense](../ide/media/template-intellisense-cpp-2.png "IntelliSense šablony seznamu výsledků")

Okno v dolní části editoru ukazuje, kde každá instance byl nalezen a jaké byly svých argumentů.

![C&#43; &#43; mapy vytváření instancí šablony IntelliSense](../ide/media/template-intellisense-cpp-4.png "mapy vytváření instancí šablony IntelliSense")

**Šablona panel** informace je považován za konkrétní uživatele. Je uložen ve složce .vs a není potvrzena do správy zdrojového kódu.

##  <a name="error-squiggles-and-quick-fixes"></a>Podtržení vlnovkou u chyb a rychlých oprav

Pokud editor zjistí problémy s vaším kódem, přidá barevné podtržení vlnovkou podle problému. Označuje červenou vlnovkou kód, který nebude kompilovat. Zelenou vlnovkou znamenat další druhy problémů, které mohou být stále závažné. Můžete otevřít **seznam chyb** okna, chcete-li získat další informace o problémech.

Pro některé typy chyb stejně jako společné psaní kódu, editoru nabídne **Quick Fix** v podobě žárovky, který se zobrazí při najetí myší na piktogram. Klikněte na šipku dolů, chcete-li zobrazit návrhy. 

V následujícím příkladu `vector` byla deklarovaná, ale nebyla nalezena žádná definice, tak editor nabízí zahrnout nezbytné hlavičkový soubor:

![C&#43; &#43; Rychlá oprava](../ide/media/quick-fix-for-header-cpp.png " C++ Rychlá oprava")

Editor také nabízí rychlé opravy pro některé refaktoringu příležitosti. Například pokud deklarujete třídu v souboru hlaviček, Visual Studio nabídne k vytvoření definice pro něj v souboru s příponou .cpp samostatné. 

![C&#43; &#43; Rychlá oprava](../ide/media/quick-fix.png " C++ Rychlá oprava")

## <a name="change-tracking"></a>Sledování změn

Pokaždé, když provedete změnu souboru, se zobrazí žlutý pruh na levé straně k označení, že byly provedeny všechny neuložené změny. Při ukládání souboru se panel zbarví zeleně. Pruhy zelené a žlutý jsou zachovány jako dokument je otevřen v editoru. Představují změny provedené od posledního otevření dokumentu.

![C&#43; &#43; sledování změn](../ide/media/change-tracking-cpp.png "Change tracking")

## <a name="move-code"></a>Přesunout kód

Řádků kódu můžete přesunout nahoru nebo dolů, že je vyberete, podržíte Alt a stisknutím klávesy **spuštěno/mimo provoz** klávesy se šipkami.

##  <a name="insert-snippets"></a>Vložte fragmenty kódu

Fragment kódu je předdefinovaný část zdrojového kódu. Klikněte pravým tlačítkem na jednom místě nebo vybraný text k vložení fragmentu kódu nebo obklopit fragmentem vybraný text. Následující obrázek ukazuje tři kroky ohraničit vybraný příkaz s smyčky for. Jsou žlutým zvýrazněním v konečném obrazu upravitelná pole, které přistupujete pomocí klávesy tab. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

![C&#43;&#43; Insert Snippet Drop&#45;down](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>Přidat třídu

Přidejte novou třídu z **projektu** nabídky, nebo z místní nabídky v **Průzkumníka řešení**:

![Přidejte novou třídu v jazyce C&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Můžete také použít Průvodce třídami změnit nebo zkontrolovat existující třídy.

![C&#43; &#43; třídy Průvodce](../ide/media/vs2017-class-wizard.png)

Další informace najdete v tématu [přidání funkce pomocí průvodců kódem (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="refactoring"></a>Refaktoring

Refaktoring jsou k dispozici v místní nabídce rychlá akce, nebo kliknutím na [žárovky](/visualstudio/ide/perform-quick-actions-with-light-bulbs) v editoru.  Některé jsou taky součástí **Upravit > Refaktorovat** nabídky.  Tyto funkce patří:

* [Přejmenovat](refactoring/rename.md)
* [Extrahovat funkci](refactoring/extract-function.md)
* [Implementovat čistě virtuální](refactoring/implement-pure-virtuals.md)
* [Vytvořit deklaraci/definici](refactoring/create-declaration-definition.md)
* [Přesunout – definice funkce](refactoring/move-definition-location.md)
* [Převod na nezpracovaný řetězcový literál](refactoring/convert-to-raw-string-literal.md)
* [Změnit signaturu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Vynucení stylu kódu s ClangFormat a EditorConfig

Visual Studio 2017 a novější se dodává s integrovanou podporou pro [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), Oblíbené formátování kódu nástroj, který C++ založené na Clang/LLVM. Zadejte "ClangFormat" do [Snadné spuštění](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) ji chcete použít jeden z těchto běžných formátů:

- LLVM
- Google
- Chromu
- Mozilla
- Komponenty WebKit
- Visual Studio

Můžete taky zadat vlastní souboru .clang-format nebo _clang-format platí vlastní pravidla pro všechny soubory kódu na stejné úrovni nebo verzi uvedenou níže.

Soubory jsou snadno sdílet přes správu zdrojových kódů, takže můžete vynutit konvence psaní kódu celého celého vývojového týmu.

![C&#43; &#43; Clang formátu](../ide/media/clang-format-cpp.png "Clang formátu")

Visual Studio 2017 a novější podporuje také [EditorConfig](https://editorconfig.org/), která funguje podobným způsobem. ClangFormat, ale má více možností stylu než EditorConfig, včetně pravidel, které jsou specifické pro C++. S **EditorConfig**, vytvoříte **.editorconfig** soubory a umístit je do jiné složky vašeho základu kódu k určení styly kódu pro tyto složky a jejich podsložky. **.Editorconfig** souboru nahrazuje jiné **.editorconfig** soubory v nadřazené složky a přepíše jakékoli nastavení formátování nakonfigurovat přes **nástroje**  >  **Možnosti**. Můžete nastavit pravidla pro karty vs. mezery, velikost odsazení a další. Další informace najdete v tématu [vytvořit nastavení přenosné vlastního editoru pomocí řešení EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Další možnosti formátování

**Snadné spuštění** vyhledávacího pole poskytuje nejrychlejší způsob, jak najít nastavení nebo nástroj. Je umístěn v hlavní nabídce. Stačí začít psát a automatické dokončování seznam bude filtrovat výsledky.

![Snadné spuštění sady Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "snadného spuštění")

Chcete-li nastavit možnosti, jako je například odsazení, uzavírání hranatých závorek a barevné zvýraznění formátování, zadejte "C++ formát" do **Snadné spuštění** okna.

![Možnosti formátování pro C++](media/cpp-formatting-options.png)

Další možnosti formátování jsou nalezené pod **upravit** > **Upřesnit** v hlavní nabídce.

![C++pokročilé možnosti úprav](media/edit-advanced-cpp.png)

Možnosti pro povolení a konfigurace C++-konkrétní funkce úprav jsou umístěny v **nástroje** > **možnosti** > **textový Editor**  >  **C /C++** . Po výběru možnosti, kterou chcete nastavit, můžete získat další nápovědu stisknutím kombinace kláves **F1** při dialogového okna je aktivní. Obecné možnosti formátování kódu, zadejte `Editor C++` do **Snadné spuštění**.

![Visual Studio Tools > Options](../ide/media/tools-options.png "Editor options")

Seznámit s experimentálními funkcemi, které mohou nebo nemusí být zahrnuté v budoucí verzi systému Visual Studio, najdete v [textového editoru C++ experimentální](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) dialogového okna. V sadě Visual Studio 2017 a novější můžete povolit **prediktivní IntelliSense** v tomto dialogovém okně.

## <a name="see-also"></a>Viz také

[Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>
[Procházet vaše C++ kódové základny v sadě Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s živými sdílenou složkou proC++](live-share-cpp.md)