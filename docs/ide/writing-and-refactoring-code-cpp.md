---
title: Úpravy a refaktorace C++ kódu v aplikaci Visual Studio
description: Pomocí editoru C++ kódu v aplikaci Visual Studio můžete formátovat, Procházet, pochopit a Refaktorovat kód.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: 6d920ec302e8385d900d74152ee5ad17851fdaac
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077850"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Úpravy a refaktorace C++ kódu v aplikaci Visual Studio

Visual Studio poskytuje několik nástrojů, které vám pomůžou psát, upravovat a Refaktorovat kód.

##  <a name="intellisense"></a>IntelliSense

IntelliSense je výkonný nástroj pro dokončování kódu, který navrhuje symboly a fragmenty kódu při psaní. C++Technologie IntelliSense v aplikaci Visual Studio běží v reálném čase a analyzuje základ kódu při jejich aktualizaci a poskytování doporučení. Při psaní více znaků se seznam doporučených výsledků zúží dolů.

![Rozevírací&#43; &#43; seznam členů C](../ide/media/cpp-statement-completion.png)

Některé symboly jsou automaticky vynechány, aby lépe omezily výsledky. Například při přístupu ke členům objektu třídy z vnějšku třídy nebudete moci zobrazit soukromé členy ve výchozím nastavení nebo chráněných členů (Pokud nejste v kontextu podřízené třídy). Filtrování můžete upravit pomocí tlačítek v dolní části.

Když v rozevíracím seznamu vyberete symbol, můžete ho automaticky zadat pomocí **tabulátoru**, **zadáním**nebo jednoho z dalších znaků potvrzení (ve výchozím nastavení: `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \`). Chcete-li přidat nebo odebrat znaky z tohoto seznamu, vyhledejte "IntelliSense" v **panelu snadného spuštění** (CTRL + Q) a vyberte **textový editor >C++ možnosti upřesnit v jazyce C/>** . Možnost v **seznamu členů seznam znaků potvrzení** vám umožní přizpůsobit seznam požadovanými změnami.

Možnost **režim filtrování seznamu členů** určuje, jaké druhy návrhů automatického dokončování IntelliSense vidíte. Ve výchozím nastavení je nastavená na **fuzzy**. Pokud máte symbol nazvaný *MyAwesomeClass*, můžete při hledání přibližně zadat "Mac" a najít třídu v návrzích automatického dokončování. Nepřibližný algoritmus nastaví minimální prahovou hodnotu, kterou symboly musí splňovat, aby se v seznamu zobrazily. **Inteligentní** filtrování zobrazí všechny symboly obsahující podřetězce, které odpovídají zadaným hodnotám. Filtrování **předpon** vyhledá řetězce, které začínají zadaným textem.

Další informace o C++ technologii IntelliSense naleznete v tématu [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) a [konfigurace C++ projektu pro technologii IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

IntelliCode je technologie IntelliSense s asistencí AI. Nejpravděpodobnější kandidát v horní části seznamu dokončení. Doporučení IntelliCode jsou založená na tisících open source projektů na GitHubu s více než 100 hvězdičkami. V kombinaci s kontextem kódu je seznam pro doplňování přizpůsobený pro podporu běžných postupů.

Při psaní C++bude IntelliCode pomáhat při používání oblíbených knihoven, jako je C++ standardní knihovna. Kontext kódu slouží jako první k poskytnutí nejužitečnější doporučení. V následujícím příkladu se členská funkce `size` obvykle používá s funkcí `sort`, takže je umístěná v horní části seznamu výsledků.

![IntelliCode&#43; &#43; jazyka C](../ide/media/intellicode-cpp.png "C++IntelliCode")

::: moniker range="vs-2019"

V aplikaci Visual Studio 2019 je IntelliCode k dispozici jako volitelná komponenta v úloze  **C++ vývoj desktopových** aplikací. Pokud se chcete ujistit, že je IntelliCode C++aktivní pro, vyhledejte v **nabídce nástroje** > **Možnosti** > **IntelliCode** > **Obecné** a nastavte  **C++ základní model** na **povoleno**.

::: moniker-end

::: moniker range="vs-2017"

V aplikaci Visual Studio 2017 je IntelliCode k dispozici jako rozšíření v Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>Prediktivní technologie IntelliSense (experimentální)

**Prediktivní technologie IntelliSense** je experimentální funkce, která používá kontextové povědomí k omezení počtu výsledků zobrazených v rozevíracím seznamu technologie IntelliSense. Algoritmus používá porovnávání typů, takže zobrazuje pouze výsledky, které odpovídají očekávanému typu. V nejjednodušším případě, pokud zadáte `int x =` a vyvoláte rozevírací nabídku technologie IntelliSense, uvidíte pouze celá čísla nebo funkce vracející celá čísla. Tato funkce je ve výchozím nastavení vypnutá, protože stále probíhá vývoj. Funguje nejlépe s globálními symboly; Členské funkce ještě nejsou podporované. Můžete ji zapnout zadáním "prediktivního" na **panelu snadného spuštění** nebo tak, že přejdete na **nástroje** > **Možnosti** > **textový editor** > **C/C++**  > **experimentální** > **Povolit prediktivní IntelliSense**.

Chcete-li přepsat **prediktivní technologii IntelliSense** a zobrazit seznam delší, stiskněte klávesovou **zkratku CTRL + J**. Pokud je **prediktivní technologie IntelliSense** zapnutá, volání **CTRL + J** odebere prediktivní filtr. Stisknutím **kombinace kláves CTRL + J** znovu odeberete filtr dostupnosti z výsledků seznamu členů, kde to bude relevantní. Tlačítko ([+]) v rozevíracím seznamu IntelliSense má stejný úkol jako **CTRL + J**. Když najedete myší na tlačítko, zobrazí se informace o tom, co se zobrazuje.

![Prediktivní&#43; &#43; IntelliSense v jazyce C](../ide/media/predictive-intellisense-cpp.png "Prediktivní technologie IntelliSense")

Předchozí snímek obrazovky ukazuje několik tlačítek pod rozevíracím seznamem. Tyto funkce umožňují filtry IntelliSense pro různé druhy výsledků:

- Proměnné a konstanty
- Functions
- Typy
- Makra
- Výčty
- Obory názvů

Tlačítko se zobrazí pouze v případě, že je relevantní pro vaši aktuální relaci technologie IntelliSense. Obvykle se všechna tlačítka nezobrazí současně.

## <a name="template-intellisense"></a>IntelliSense šablony

Když je kurzor uvnitř definice šablony, zobrazí se **panel šablony** , který umožňuje poskytnout ukázkové argumenty šablony pro technologii IntelliSense.

![IntelliSense&#43; &#43; – šablona jazyka C – zobrazit existující instance](../ide/media/template-intellisense-cpp-1.png "Šablona IntelliSense – zobrazit existující instance")

Kliknutím na ikonu **\<t >** rozbalíte nebo sbalíte **panel šablon**. Kliknutím na ikonu tužky nebo dvojitým kliknutím na **panel šablon** otevřete okno **Upravit** .

![IntelliSense&#43; &#43; – šablona jazyka C](../ide/media/template-intellisense-cpp-3.png "IntelliSense šablony")

Úpravy, které provedete v okně, se aplikují přímo na zdrojový kód, abyste viděli účinky v reálném čase.

Panel šablon může automaticky naplnit kandidáty na základě vytváření instancí v kódu. Kliknutím na **Přidat všechny existující instance** zobrazíte seznam všech konkrétních argumentů, které byly použity k vytvoření instance šablony v rámci vašeho základu kódu.

![Seznam&#43; &#43; výsledků technologie IntelliSense pro šablony jazyka C](../ide/media/template-intellisense-cpp-2.png "Seznam výsledků šablony IntelliSense")

Okno v dolní části editoru ukazuje, kde byla nalezena každá instance a jaké argumenty byly.

![Mapa&#43; &#43; vytváření instancí IntelliSense v šabloně jazyka C](../ide/media/template-intellisense-cpp-4.png "Mapa vytváření instancí pro šablonu IntelliSense")

Informace na **panelu šablon** se považují za specifické pro uživatele. Je uložen ve složce. vs a není svěřen do správy zdrojových kódů.

##  <a name="error-squiggles-and-quick-fixes"></a>Chyby vlnovkou a rychlé opravy

Pokud editor detekuje problémy s vaším kódem, přidá se v rámci problému barevné vlnovky. Červené vlnovky označují kód, který se nebude kompilovat. Zelené vlnovky označují jiné druhy problémů, které mohou být stále závažné. Chcete-li získat další informace o problémech, můžete otevřít okno **Seznam chyb** .

V případě některých druhů chyb a také běžných vzorů kódování bude editor nabízet **rychlou opravu** ve formě žárovky, která se zobrazí, když najedete myší na vlnovku. Kliknutím na šipku dolů zobrazíte návrhy.

V následujícím příkladu byla deklarována `vector`, ale nebyla nalezena žádná definice, takže Editor nabízí zahrnutí potřebného hlavičkového souboru:

![Rychlá&#43; &#43; oprava jazyka C](../ide/media/quick-fix-for-header-cpp.png "C++Rychlá oprava")

Editor také nabízí rychlé opravy pro některé příležitosti refaktoringu. Například pokud deklarujete třídu v hlavičkovém souboru, Visual Studio nabídne vytvoření definice v samostatném souboru. cpp.

![Rychlá&#43; &#43; oprava jazyka C](../ide/media/quick-fix.png "C++Rychlá oprava")

## <a name="change-tracking"></a>Sledování změn

Pokaždé, když provedete změnu souboru, zobrazí se na levé straně žlutý pruh, který indikuje, že byly provedeny neuložené změny. Po uložení souboru se změní pruh na zelenou. Zelené a žluté pruhy jsou zachovány, dokud je dokument otevřen v editoru. Představují změny, které byly provedeny od posledního otevření dokumentu.

![Sledování&#43; &#43; změn v jazyce C](../ide/media/change-tracking-cpp.png "Sledování změn")

## <a name="move-code"></a>Přesunout kód

Řádky kódu můžete přesunout nahoru a dolů tak, že je vyberete, podržíte klávesu Alt a stisknete klávesy se šipkami **nahoru/dolů** .

##  <a name="insert-snippets"></a>Vložit fragmenty

Fragment kódu je předdefinovaná část zdrojového kódu. Kliknutím pravým tlačítkem myši na jeden nebo vybraný text buď vložte fragment nebo Obklopte vybraný text pomocí fragmentu. Následující ilustrace znázorňuje tři kroky pro obklopení vybraného příkazu pomocí smyčky for. Žluté světla v konečném obrázku jsou upravitelná pole, ke kterým přistupujete pomocí klávesy TAB. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

![C&#43; &#43; vložit rozevírací seznam&#45;fragmentů](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>Přidat třídu

Přidejte novou třídu z nabídky **projekt** nebo z kontextové nabídky v **Průzkumník řešení**:

![Přidat novou třídu v jazyce C&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

Můžete také použít Průvodce třídou pro úpravu nebo přezkoumání existující třídy.

![Průvodce&#43; &#43; třídami jazyka C](../ide/media/vs2017-class-wizard.png)

Další informace najdete v tématu [Přidání funkcionality pomocí průvodcůC++kódem ()](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="refactoring"></a>Refaktoring

Refaktoring je k dispozici v místní nabídce rychlá akce nebo kliknutím [na žárovku v editoru](/visualstudio/ide/perform-quick-actions-with-light-bulbs) .  Některé jsou také k dispozici v nabídce **upravit > refaktoring** .  Mezi tyto funkce patří:

* [Přejmenovat](refactoring/rename.md)
* [Extrahovat funkci](refactoring/extract-function.md)
* [Implementovat čistě virtuální](refactoring/implement-pure-virtuals.md)
* [Vytvořit deklaraci/definici](refactoring/create-declaration-definition.md)
* [Přesunout – definice funkce](refactoring/move-definition-location.md)
* [Převod na nezpracovaný řetězcový literál](refactoring/convert-to-raw-string-literal.md)
* [Změnit signaturu](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Vynucování stylu kódu pomocí ClangFormat a EditorConfig

Visual Studio 2017 a novější přináší integrovanou podporu pro [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), oblíbený nástroj pro formátování kódu pro C++ založen na Clang/LLVM. Zadejte "ClangFormat" do [snadného spuštění](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) a nastavte ho tak, aby používal jeden z těchto běžných formátů:

- LLVM
- Google
- Chróm
- Mozilla
- WebKit
- Visual Studio

Můžete také zadat vlastní soubor. Clang-Format nebo _clang-Format pro použití vlastních pravidel pro všechny soubory kódu na stejné nebo nižší úrovni.

Soubory je možné snadno sdílet přes správu zdrojového kódu, takže můžete vymáhat konvence pro kódování v celém vývojovém týmu.

![Formát&#43; &#43; C Clang](../ide/media/clang-format-cpp.png "Formát Clang")

Sada Visual Studio 2017 a novější také podporuje [EditorConfig](https://editorconfig.org/), která funguje podobným způsobem. ClangFormat má ale více možností stylu než EditorConfig, včetně pravidel, která jsou specifická pro C++. Pomocí **EditorConfig**vytvoříte soubory **. EditorConfig** a umístíte je do různých složek vašeho základu kódu, abyste určili styly kódu pro tyto složky a jejich podsložky. Soubor **. editorconfig** nahrazuje jakékoli jiné soubory **. editorconfig** v nadřazených složkách a přepíše všechna nastavení formátování konfigurovaná prostřednictvím **nástrojů** > **možností**. Můžete nastavit pravidla pro tabulátory a mezery, velikost odsazení a další. Další informace najdete v tématu [Vytvoření přenosného a vlastního nastavení editoru pomocí EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Další možnosti formátování

**Rychlé spuštění** vyhledávacího pole poskytuje nejrychlejší způsob, jak najít nastavení nebo nástroj. Je umístěn v hlavní nabídce. Stačí začít psát a seznam automatického dokončování bude filtrovat výsledky.

![Snadné spuštění sady Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "Snadné spuštění")

Chcete-li nastavit možnosti formátování, jako jsou odsazení, dokončování závorek a zabarveníC++ , zadejte text "formátování" do okna **Snadné spuštění** .

![C++možnosti formátování](media/cpp-formatting-options.png)

Další možnosti formátování najdete v části **upravit** > **Upřesnit** v hlavní nabídce.

![C++Rozšířené možnosti úprav](media/edit-advanced-cpp.png)

Možnosti pro povolení a konfiguraci C++specifických funkcí pro úpravy jsou k dispozici v části **nástroje** > **Možnosti** > **textový editor** > **C/C++** . Po výběru možnosti, kterou chcete nastavit, můžete získat další pomoc stisknutím **klávesy F1** , když je dialog aktivní. Pro obecné možnosti formátování kódu zadejte `Editor C++` do panelu snadného **spuštění**.

![Možnosti > Visual Studio Tools](../ide/media/tools-options.png "Možnosti editoru")

Experimentální funkce, které mohou nebo nemusí být zahrnuty v budoucí verzi sady Visual Studio, najdete v dialogovém okně [experimentální textový editor C++ ](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) . V aplikaci Visual Studio 2017 a novější můžete v tomto dialogovém okně Povolit **prediktivní IntelliSense** .

## <a name="see-also"></a>Viz také

[Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>
[Procházení základu C++ kódu v aplikaci Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s Live Share proC++](live-share-cpp.md)
