---
title: Úprava a refaktoring kódu Jazyka C++ v sadě Visual Studio
description: Pomocí editoru kódu Jazyka C++ ve Visual Studiu můžete formátovat, procházet, chápat a refaktorovat kód.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: 070c79e02f6e05adeda5f17a0dde02afdf22703b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353747"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Úprava a refaktoring kódu Jazyka C++ v sadě Visual Studio

Visual Studio poskytuje několik nástrojů, které vám pomohou psát, upravovat a refaktorovat váš kód.

## <a name="intellisense"></a>IntelliSense

IntelliSense je výkonný nástroj pro dokončování kódu, který při psaní navrhuje symboly a fragmenty kódu. C++ IntelliSense v sadě Visual Studio běží v reálném čase, analyzuje váš základ kódu při jeho aktualizaci a poskytuje doporučení. Při psaní více znaků se seznam doporučených výsledků zužuje.

![Rozevírací seznam C&#43;&#43; členy](../ide/media/cpp-statement-completion.png)

Některé symboly jsou automaticky vynechány, aby pomohly zúžit výsledky. Například při přístupu k členům objektu třídy mimo třídu nebudete moci zobrazit soukromé členy ve výchozím nastavení nebo chráněné členy (pokud nejste v kontextu podřízené třídy). Filtrování můžete upravit pomocí tlačítek v dolní části.

Po výběru symbolu z rozevíracího seznamu jej můžete automaticky doplnit **tabulátorem**, `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \` **Enternebo**jedním z dalších znaků potvrzení (ve výchozím nastavení: ). Chcete-li přidat nebo odebrat znaky z tohoto seznamu, vyhledejte v **doplňku Snadné spuštění** (Ctrl + Q) položku "IntelliSense" a zvolte možnost **Textový editor > C/C++ > Upřesnit.** Možnost **Znaky potvrzení seznamu členů** umožňuje přizpůsobit seznam požadovanými změnami.

Možnost **Režim filtru seznamu členů** určuje, jaké typy návrhů automatického dokončování technologie IntelliSense se zobrazují. Ve výchozím nastavení je nastavena na **přibližné**. V fuzzy vyhledávání, pokud máte symbol s názvem *MyAwesomeClass*, můžete zadat "MAC" a najít třídu v návrhy automatického dokončování. Fuzzy algoritmus nastaví minimální prahovou hodnotu, kterou musí symboly splňovat, aby se v seznamu zobrazovalo. **Inteligentní** filtrování zobrazí všechny symboly obsahující podřetězce, které odpovídají zadanému textu. **Filtrování předpon** hledá řetězce, které začínají tím, co jste zadali.

Další informace o technologie C++ IntelliSense naleznete v [tématech Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) a [Configure a C++ project for IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

IntelliCode je technologie IntelliSense s asistencí umělé aumělé žene. To staví nejpravděpodobnější kandidát na začátek seznamu dokončení. Doporučení IntelliCode jsou založena na tisících open source projektů na GitHubu s více než 100 hvězdičkami. V kombinaci s kontextem vašeho kódu je seznam dokončení přizpůsoben tak, aby podporoval běžné postupy.

Při psaní Jazyka C++ bude IntelliCode pomáhat při používání oblíbených knihoven, jako je například standardní knihovna Jazyka C++. Kontext kódu se používá k poskytnutí nejužitečnější doporučení jako první. V následujícím příkladu `size` se členské funkce běžně `sort` používá s funkcí, takže se zobrazí na začátek seznamu výsledků.

![C&#43;&#43; IntelliCode](../ide/media/intellicode-cpp.png "C++ IntelliCode")

::: moniker range="vs-2019"

Ve Visual Studiu 2019 je IntelliCode k dispozici jako volitelná součást v zatížení **vývoje plochy jazyka C++.** Chcete-li se ujistit, že je intelliCode aktivní pro C++, přejděte na **Nástroje** > **Možnosti** > **IntelliCode** > **General** a nastavte základní model **C++** na **Povoleno**.

::: moniker-end

::: moniker range="vs-2017"

V Sadě Visual Studio 2017 je IntelliCode k dispozici jako rozšíření na webu Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Prediktivní technologie IntelliSense (experimentální)

**Predictive IntelliSense** je experimentální funkce, která využívá kontextové povědomí k omezení počtu výsledků zobrazených v rozevíracím seznamu Technologie IntelliSense. Algoritmus použije odpovídající typ tak, aby se zobrazí pouze ty výsledky, které odpovídají očekávanému typu. V nejjednodušším případě pokud `int x =` zadáte a vyvoláte rozevírací soubor IntelliSense, zobrazí se pouze celá čísla nebo funkce vracející celá čísla. Tato funkce je ve výchozím nastavení vypnutá, protože je stále ve vývoji. Funguje nejlépe s globálními symboly; členské funkce ještě nejsou podporovány. Můžete ji zapnout zadáním "Prediktivní" v **rychlém spuštění** nebo přejdete na **Tools** > **nástroje Možnosti** > **Textový editor** > **C / C ++** > **Experimentální** > **Povolit prediktivní IntelliSense**.

Chcete-li přepsat **prediktivní technologie IntelliSense** a zobrazit delší seznam, stiskněte **kombinaci kláves Ctrl + J**. Pokud je **zapnutá funkce Predictive IntelliSense,** vyvoláte **ctrl + j** filtr Prediktivní. Stisknutím **kláves Ctrl + J** znovu odeberete filtr usnadnění přístupu z výsledků seznamu členů, kde je to relevantní. Tlačítko ([+]) v rozevíracím seznamu Technologie IntelliSense dělá totéž jako **ctrl + j**. Najeďte nad tlačítkem a zobrazte popisek informací o tom, co se zobrazuje.

![C&#43;&#43; Prediktivní technologie IntelliSense](../ide/media/predictive-intellisense-cpp.png "Prediktivní technologie IntelliSense")

Předchozí snímek obrazovky zobrazuje několik tlačítek v rozevíracím seznamu. Tyto umožňují filtry IntelliSense pro různé druhy výsledků:

- Proměnné a konstanty
- Functions
- Typy
- Makra
- Výčty
- Jmenné prostory

Tlačítko se zobrazí pouze v případě, že je relevantní pro aktuální relaci Technologie IntelliSense. Obvykle nevidíte všechna tlačítka současně.

## <a name="template-intellisense"></a>Šablona IntelliSense

Pokud je stříška uvnitř definice šablony, zobrazí se **panel šablony,** který umožňuje zadat argumenty ukázkové šablony pro technologie IntelliSense.

![C&#43;&#43; Šablona IntelliSense Zobrazit existující koniace](../ide/media/template-intellisense-cpp-1.png "Šablona IntelliSense zobrazit existující koniace")

Klepnutím ** \<** na ikonu T>rozbalte nebo sbalte **panel šablon**. Kliknutím na ikonu tužky nebo poklepáním na **panel šablony** otevřete okno **Úpravy.**

![C&#43;&#43; šablona IntelliSense](../ide/media/template-intellisense-cpp-3.png "Šablona IntelliSense")

Úpravy, které provedete v okně, se použijí přímo na zdrojový kód, takže můžete vidět efekty v reálném čase.

Panel šablon může automaticky vyplňovat kandidáty na základě instancí ve vašem kódu. Kliknutím na **Přidat všechny existující instance zobrazíte** seznam všech konkrétních argumentů, které byly použity k vytvoření instance šablony v celém základu kódu.

![C&#43;&#43; Šablona Seznam výsledků Technologie ATelliSense](../ide/media/template-intellisense-cpp-2.png "Seznam výsledků šablony Technologie AtelliSense")

Okno v dolní části editoru ukazuje, kde byla nalezena každá instance a jaké byly jeho argumenty.

![C&#43;&#43; šablona IntelliSense Iniace Mapa](../ide/media/template-intellisense-cpp-4.png "Mapa infiace intelliSense šablony")

**Informace o panelu šablony** jsou považovány za specifické pro uživatele. Je uložen ve složce .vs a není potvrzena správy zdrojového kódu.

## <a name="error-squiggles-and-quick-fixes"></a>Chybové vlnovky a rychlé opravy

Pokud editor zjistí problémy s kódem, přidá barevné vlnovky pod problémem. Červené vlnovky označují kód, který se nezkompiluje. Zelené vlnovky označují jiné druhy problémů, které mohou být stále potenciálně závažné. Chcete-li získat další informace o problémech, můžete otevřít okno **Seznam chyb.**

U některých druhů chyb, stejně jako běžných kódovacích vzorů, nabídne editor **rychlou opravu** ve formě žárovky, která se zobrazí, když najedete nad vlnovkou. Kliknutím na šipku dolů zobrazíte návrhy.

V následujícím příkladu `vector` byla deklarována a, ale nebyla nalezena žádná definice, takže editor nabízí zahrnutí potřebného souboru záhlaví:

![C&#43;&#43; rychlá oprava](../ide/media/quick-fix-for-header-cpp.png "Rychlá oprava jazyka C++")

Editor také nabízí rychlé opravy pro některé možnosti refaktoringu. Pokud například deklarujete třídu v souboru záhlaví, visual studio nabídne vytvoření definice pro ni v samostatném souboru CPP.

![C&#43;&#43; rychlá oprava](../ide/media/quick-fix.png "Rychlá oprava jazyka C++")

## <a name="change-tracking"></a>Sledování změn

Při každé změně souboru se vlevo zobrazí žlutý pruh označující, že byly provedeny neuložené změny. Když soubor uložíte, pruh se změní na zelený. Zelené a žluté pruhy jsou zachovány tak dlouho, dokud je dokument otevřen v editoru. Představují změny, které byly provedeny od posledního otevření dokumentu.

![C&#43;&#43; sledování změn](../ide/media/change-tracking-cpp.png "Sledování změn")

## <a name="move-code"></a>Přesunout kód

Řádky kódu můžete přesouvat nahoru a dolů tak, že je vyberete, podržíte klávesu Alt a stisknete klávesy **se šipkami nahoru/dolů.**

## <a name="insert-snippets"></a>Vložení výstřižků

Úryvek je předdefinovaná část zdrojového kódu. Kliknutím pravým tlačítkem myši na jeden bod nebo na vybraný text vložíte úryvek nebo vybraný text obklopíte úryvkem. Následující obrázek znázorňuje tři kroky k obklopit vybraný příkaz s for smyčky. Žlutá zvýraznění v konečném obrázku jsou upravitelná pole, ke kterým přistupujete pomocí klávesy tabulátoru. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).

![C&#43;&#43; Vložit fragment&#45;dolů](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Přidat třídu

Přidání nové třídy z nabídky **Projekt** nebo z kontextové nabídky v **Průzkumníku řešení**:

![Přidat novou třídu v&#43;&#43;C](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Pomocí Průvodce třídou můžete také upravit nebo zkontrolovat existující třídu.

![Průvodce třídou C&#43;&#43; ](../ide/media/vs2017-class-wizard.png)

Další informace naleznete [v tématu Přidání funkcí pomocí Průvodců kódem (C++).](../ide/adding-functionality-with-code-wizards-cpp.md)

## <a name="refactoring"></a>Refaktoring

Refaktoringy jsou k dispozici v kontextové nabídce Rychlá akce nebo kliknutím na [žárovku](/visualstudio/ide/perform-quick-actions-with-light-bulbs) v editoru.  Některé se také nacházejí v nabídce **Upravit > refaktoru.**  Mezi tyto funkce patří:

- [Přejmenovat](refactoring/rename.md)
- [Extrahovat funkci](refactoring/extract-function.md)
- [Implementovat čistě virtuální](refactoring/implement-pure-virtuals.md)
- [Vytvořit deklaraci/definici](refactoring/create-declaration-definition.md)
- [Přesunout – definice funkce](refactoring/move-definition-location.md)
- [Převod na nezpracovaný řetězcový literál](refactoring/convert-to-raw-string-literal.md)
- [Změnit signaturu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Vynucení stylu kódu pomocí ClangFormat a EditorConfig

Visual Studio 2017 a novější přichází s integrovanou podporou [clangformatu](https://clang.llvm.org/docs/ClangFormat.html), oblíbeného nástroje pro formátování kódu pro C++ založeného na Clang/LLVM. Chcete-li do [panelu Snadné spuštění](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) nastavit funkci "ClangFormat", nastavte ji tak, aby používala jeden z těchto běžných formátů:

- LLVM
- Google
- Chrom
- Mozilla
- Webkit
- Visual Studio

Můžete také zadat vlastní soubor ve formátu .clang nebo _clang formátu, který použije vlastní pravidla pro všechny soubory kódu na stejné úrovni nebo nižší.

Soubory lze snadno sdílet prostřednictvím správy zdrojového kódu, takže můžete vynutit konvence kódování v celém vývojovém týmu.

![Formát clang&#43;&#43; ](../ide/media/clang-format-cpp.png "Formát Clang")

Visual Studio 2017 a novější také podporuje [EditorConfig](https://editorconfig.org/), který funguje podobným způsobem. ClangFormat má však více možností stylu než EditorConfig, včetně pravidel, která jsou specifická pro C++. Pomocí **editorconfig**vytvoříte soubory **.editorconfig** a umístíte je do různých složek základu kódu, abyste určili styly kódu pro tyto složky a jejich podsložky. Soubor **.editorconfig** nahrazuje všechny ostatní soubory **.editorconfig** v nadřazených složkách a přepíše všechna nastavení formátování nakonfigurovaná pomocí**možností** **nástrojů** > . Můžete nastavit pravidla pro karty vs. mezery, velikost odsazení a další. Další informace naleznete v [tématu Vytvoření nastavení přenosného vlastního editoru pomocí editoru EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Další možnosti formátování

Vyhledávací pole **Snadné spuštění** poskytuje nejrychlejší způsob, jak najít nastavení nebo nástroj. Nachází se v hlavním menu. Stačí začít psát a auto-dokončení seznamu bude filtrovat výsledky.

![Snadné spuštění sady Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "Snadné spuštění")

Chcete-li nastavit možnosti formátování, například odsazení, dokončení složených závorek a vybarvení, zadejte do okna **Snadné spuštění** text Formátování Jazyka C++.

![Možnosti formátování jazyka C++](media/cpp-formatting-options.png)

Další možnosti formátování najdete v části **Upravit** > **upřesnit** v hlavní nabídce.

![Rozšířené možnosti úprav jazyka C++](media/edit-advanced-cpp.png)

Možnosti povolení a konfigurace funkcí úprav specifických pro C++jsou **umístěny** > v části Tools**Options** > **Text Editor** > **C/C++**. Po výběru možnosti, kterou chcete nastavit, můžete získat další nápovědu stisknutím **klávesy F1,** když je dialog zaostřený. Možnosti formátování obecného kódu `Editor C++` napište do **panelu Snadné spuštění**.

![Nástroje sady Visual Studio > možnosti](../ide/media/tools-options.png "Možnosti editoru")

Experimentální funkce, které mohou nebo nemusí být zahrnuty v budoucí verzi sady Visual Studio, se nacházejí v dialogovém okně [Experimentovat s textovým editorem C++.](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) V sadě Visual Studio 2017 a novějších můžete v tomto dialogovém okně povolit **prediktivní technologie IntelliSense.**

## <a name="see-also"></a>Viz také

[Čtení a pochopení kódu C++](read-and-understand-code-cpp.md)</br>
[Navigace v základu kódu Jazyka C++ v sadě Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s live share pro C++](live-share-cpp.md)
