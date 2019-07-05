---
title: Přejděte C++ kódu v sadě Visual Studio
description: Použít různé nástroje v sadě Visual Studio k navigaci v vaše C++ základu kódu.
ms.date: 05/28/2019
ms.openlocfilehash: c2d3a1aa4a26cb820ff4a1e87d6eae88b1b8e739
ms.sourcegitcommit: 96f48079cdc402e4c2c1578d1f1eed4846a484dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2019
ms.locfileid: "67576530"
---
# <a name="navigate-c-code-in-visual-studio"></a>Přejděte C++ kódu v sadě Visual Studio

Visual Studio poskytuje sadu nástrojů, které můžete použít k navigaci v vašeho základu kódu rychle a efektivně.

## <a name="open-an-included-file"></a>Otevřete vkládaného souboru

Klikněte pravým tlačítkem na `#include` směrnice a vyberte **přejít do dokumentu**. Nebo vyberte **F12** s kurzorem přes tento řádek k otevření souboru.

![C&#43; &#43; možnost nabídky přejít do dokumentu](../ide/media/go-to-document.png "přejít do dokumentu")

## <a name="toggle-headercode-file"></a>Přepínač záhlaví/kódový soubor

Můžete přepínat mezi záhlaví souboru a jeho odpovídající zdrojový soubor. Klikněte pravým tlačítkem na libovolné místo v souboru a vyberte **přepínač záhlaví/kódový soubor**. Nebo můžete vybrat **Ctrl + K**, **Ctrl + O**.

## <a name="go-to-definitiondeclaration"></a>Přejít na definice nebo deklarace

Můžete přejít k definici symbolu kódu v editoru pravým tlačítkem a vyberete **přejít k definici**, nebo výběrem **F12**. Můžete přejít na deklaraci podobně kliknutím pravým tlačítkem a otevřete kontextu nabídku, nebo výběrem **Ctrl + F12**.

![C&#43; &#43; přejít k definici](../ide/media/go-to-def.png "přejít k definici")

## <a name="go-to"></a>Přejít na

**Přejít na** odkazuje na sadu funkcí, že každá z nichž poskytuje zvláštní druh výsledek na základě filtrů můžete zadat navigace. 

Můžete otevřít **přejít na** s **Ctrl +** . Tato akce vytvoří vyhledávací pole v dokumentu, který upravujete.

![C&#43; &#43; přejít na](../ide/media/go-to-cpp.png "přejít na")

**Přejít na** zahrnuje tyto filtry hledání:

- **Přejít na řádek** (**Ctrl + G**): Rychle přejděte na jiný řádek v aktuálním dokumentu.
- **Přejít ke všem** (**Ctrl +** ) nebo (**Ctrl + T**): Výsledky hledání obsahují vše, co následuje.
- **Přejděte na soubor** (**Ctrl 1, F**): Vyhledávání souborů ve vašem řešení.
- **Přejděte na typ** (**Ctrl 1, T**): Výsledky hledání obsahují:
  - Třídy, struktury a výčty.
  - Rozhraní a delegátů (pouze pro spravovaný kód).
- **Přejděte na člen** (**Ctrl 1, M**): Výsledky hledání obsahují:
  - Globální proměnné a globální funkce.
  - Členské proměnné třídy a členské funkce.
  - Konstanty.
  - Položky výčtu.
  - Vlastnosti a události.
- **Přejděte na Symbol** (**Ctrl 1, S**): Výsledky hledání obsahují:
  - Výsledky z přejít na typy a přejděte na členy.
  - Všechny zbývající C++ jazykovým konstrukcím, včetně maker.

Při prvním vyvolání **přejít na** s **Ctrl +** , **přejít na vše** je aktivováno (žádné filtry na výsledky hledání). Pak můžete vybrat filtr, který chcete pomocí tlačítek téměř do vyhledávacího pole. Můžete vyvolat konkrétní filtr pomocí jeho odpovídající klávesové zkratky. To tedy otevře **přejít na** vyhledávací pole s tímto filtrem předem vybrali. Všechny klávesové zkratky se dají konfigurovat.

Použít filtr text, začněte s odpovídající znak tohoto filtru, za nímž následuje mezera vašemu vyhledávacímu dotazu. (**Přejít na řádek** můžete volitelně vynechat, nechte pole.) K dispozici jsou tyto filtry textu:

- Přejít na vše: (žádný filtr text)
- Přejděte na číslo řádku::
- Přejděte k souboru: f
- Přejděte na typu: t
- Přejděte na člen: m
- Přejděte na Symbol: #

Následující příklad ukazuje výsledky z *přejít na soubory* operace pomocí filtru "f":

![C&#43; &#43; přejděte do nabídky](../ide/media/vs2017-go-to-results.png "přejděte do nabídky")

Chcete-li zobrazit seznam filtrech textu, zadejte? následovanými mezerou. Můžete také přejít **přejít na** příkazů s **upravit** nabídky. Toto je další způsob, jak připomenou hlavní **přejít na** klávesové zkratky.

![C&#43; &#43; přejděte do nabídky](../ide/media/go-to-menu-cpp.png "přejděte do nabídky")

## <a name="find-or-find-in-files"></a>Najít nebo najít v souborech

Hledání textu pro všechno, co můžete spustit ve vašem řešení pomocí **najít** (**Ctrl + F**) nebo **najít v souborech** (**Ctrl + Shift + F**).

**Najít** se dají vymezit na výběr, aktuální dokument, všechny otevřené dokumenty, aktuální projekt nebo celé řešení. Můžete použít regulární výrazy a prostý text. Také zvýrazní všechny shody automaticky v integrovaném vývojovém prostředí.

![C&#43; &#43; najít](../ide/media/find-cpp.png "najít")

**Najít v souborech** je výkonnější verze **najít** , který zobrazí výsledky v **výsledky hledání** okna. Můžete hledat závislosti externí kód, filtrovat podle typů souborů a další. 

![C&#43; &#43; najít v souborech](../ide/media/find-in-files-cpp.png "najít v souborech")

Můžete uspořádat **najít v souborech** výsledkem dvě okna. Výsledky z více vyhledávání, můžete připojit společně. Vyberte příslušný výsledek přejdete do tohoto umístění v souboru.

![C&#43; &#43; najít v souborech](../ide/media/vs2017-find-in-files-results.png "najít v souborech")

Další informace najdete v tématu [najít v souborech](/visualstudio/ide/find-in-files) v dokumentaci k sadě Visual Studio.

## <a name="find-all-references"></a>Najít všechny odkazy

Pokud chcete najít všechny použití symbolu ve vašem základu kódu, umístíte blikající kurzor v nebo bezprostředně po symbolu, klikněte pravým tlačítkem a pak vyberte **najít všechny odkazy**. Filtrování, řazení nebo seskupení výsledků mnoha různými způsoby. Výsledky naplnit postupně. Se už klasifikován jako čte nebo zapisuje do pomoct zjistit, co je v řešení na rozdíl od systémových hlavičkách nebo jiných knihoven.

![C&#43; &#43; najít všechny odkazy](../ide/media/find-all-references-results-cpp.png "najít všechny odkazy")

Seskupení výsledků podle těchto kategorií:

- Projekt a pak definice
- Jenom definice
- Definice a pak projekt
- Definice a pak cesta
- Definice, projekt a pak cesta

 #### <a name="filter-results"></a>Filtrování výsledků

Pro filtrování výsledků, najeďte myší na sloupec a vyberte ikonu filtrování, která se otevře. Můžete filtrovat výsledky z prvního sloupce, chcete-li skrýt věci jako odkazy na řetězec a komentáře, které nebudete chtít naleznete v tématu.

![C&#43; &#43; najít všechny odkazy na filtry](../ide/media/find-all-references-filters-cpp.png "najít všechny odkazy na filtry")

- **Potvrdit výsledky**: Skutečný kód odkazy na symbol vyhledaly. Například hledání členská funkce volána `Size` vrátí všechny odkazy na `Size` , které odpovídají oboru třídy, která definuje `Size`.

- **Nepotvrzený výsledky**: Tento filtr je vypnuto ve výchozím nastavení protože zobrazuje symboly, jejíž název odpovídá ale nejsou skutečné odkazy na symbol, který hledáte. Například, pokud máte dvě třídy, z nichž každý definuje členskou funkci volat `Size`, a spusťte hledání `Size` na odkaz z objektu `Class1`, všechny odkazy na `Size` z `Class2` zobrazí jako Nepotvrzený.

- **Nezpracované výsledky**: **Najít všechny odkazy** operace může trvat dobu na větší základů kódu, takže v seznamu výsledků se zobrazí "nezpracované" výsledky. Nezpracované výsledky odpovídat názvu symbolu vyhledávaná, ale dosud nebyla potvrzena jako odkazy na skutečný kód. Tento filtr se získat rychlejší výsledky, můžete zapnout. Právě mějte na paměti, že některé výsledky nemusí být skutečný odkazy.

 #### <a name="sort-results"></a>Řazení výsledků

Výsledky můžete řadit podle libovolného sloupce tak, že vyberete tento sloupec. Můžete přepínat mezi vzestupném nebo sestupném pořadí tak, že znovu vyberete sloupec.

## <a name="navigation-bar"></a>Navigační panel

Můžete přejít na definici typu v souboru nebo členy, s použitím typu **navigační panel** , který je uveden výše v okně editoru.

![C&#43; &#43; navigační panel](../ide/media/navbar-cpp.png "navigační panel")

## <a name="see-also"></a>Viz také:

- [Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>
- [Upravit a Refaktorovat C++ kódu](read-and-understand-code-cpp.md)</br>
- [Spolupráce s živými sdílenou složkou proC++](live-share-cpp.md)
