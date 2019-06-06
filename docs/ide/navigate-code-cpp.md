---
title: Přejděte C++ kódu v sadě Visual Studio
description: Použít různé nástroje v sadě Visual Studio k navigaci v vaše C++ základu kódu.
ms.date: 05/28/2019
ms.openlocfilehash: 5f01307cc82fb1e61ba6fd0c922ea376279fba8b
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743384"
---
# <a name="navigate-c-code-in-visual-studio"></a>Přejděte C++ kódu v sadě Visual Studio

Visual Studio poskytuje sadu nástrojů k tomu, abyste k navigaci v vašeho základu kódu rychle a efektivně.

## <a name="open-an-included-file"></a>Otevřete vkládaného souboru

Klikněte pravým tlačítkem na `#include` – direktiva a zvolte **přejít do dokumentu**, nebo stiskněte klávesu **F12** s kurzorem přes tento řádek k otevření souboru.

![C&#43; &#43; možnost nabídky přejít do dokumentu](../ide/media/go-to-document.png "přejít do dokumentu")

## <a name="toggle-headercode-file"></a>Přepínač záhlaví/kódový soubor

Můžete přepínat mezi záhlaví souboru a jeho odpovídající zdrojový soubor, tak, že kliknete pravým tlačítkem kamkoli v souboru a zvolíte **přepínač záhlaví / soubor s kódem** nebo stisknutím klávesy **Ctrl + K, Ctrl + O**.

## <a name="go-to-definitiondeclaration"></a>Přejít na definice nebo deklarace

Můžete přejít k definici symbolu kódu v editoru pravým tlačítkem a výběrem **přejít k definici**, nebo stisknutím klávesy **F12**. Můžete přejít na deklaraci podobně jako v místní nabídce klikněte pravým tlačítkem nebo stisknutím klávesy **Ctrl + F12**.

![C&#43; &#43; přejít k definici](../ide/media/go-to-def.png "přejít k definici")

## <a name="go-to"></a>Přejít na

**Přejít na** odkazuje na sadu funkcí, že každá z nichž poskytuje zvláštní druh výsledek na základě filtrů můžete zadat navigace. 

Můžete otevřít **přejít na** s **Ctrl +,** . Tím se vytvoří vyhledávací pole v dokumentu, který upravujete.

![C&#43; &#43; přejít na](../ide/media/go-to-cpp.png "přejít na")

**Přejít na** zahrnuje tyto filtry hledání:

- **Přejít na řádek (Ctrl + G)** : rychle přejít na jiný řádek v aktuálním dokumentu
- **Přejít na všechno (Ctrl +,)** nebo **(Ctrl + T)** : výsledky hledání obsahují všechno, co níže
- **Přejděte do souboru (Ctrl 1, F)** : vyhledávání souborů ve vašem řešení
- **Přejít na typ (Ctrl 1, T)** : výsledky hledání obsahují:
  - Třídy, struktury, výčty
  - Rozhraní a delegátů (pouze pro spravovaný kód)
- **Přejít na člena (Ctrl 1, M)** : výsledky hledání obsahují:
  - Globální proměnné a globální funkce
  - Členské proměnné třídy a členské funkce
  - Konstanty
  - Položky výčtu
  - Vlastnosti a události.
- **Přejděte k symbolu (Ctrl 1, S)** : výsledky hledání obsahují:
  - Výsledky z přejít na typy a přejděte na členy
  - Všechny zbývající C++ jazykovým konstrukcím, včetně maker

Při prvním vyvolání **přejít na** s **Ctrl +** , **přejít na vše** je aktivováno (žádné filtry na výsledky hledání). Pomocí tlačítka vedle textového pole hledání můžete pak vyberte požadovaného filtru. Můžete vyvolat konkrétní filtr pomocí jeho odpovídající klávesové zkratky. Způsobem tak otevře **přejít na** vyhledávací pole s tímto filtrem předem vybraná. Všechny klávesové zkratky se dají konfigurovat.

Použít filtr text, začněte s odpovídající znak tohoto filtru, za nímž následuje mezera vašemu vyhledávacímu dotazu. (**Přejít na řádek** můžete volitelně vynechat, nechte pole.) Toto jsou k dispozici textové filtry:

- Přejít na vše: (žádný filtr text)
- Přejděte na číslo řádku::
- Přejděte k souboru: f
- Přejděte na typu: t
- Přejděte na člen: m
- Přejděte na Symbol: #

Následující příklad ukazuje výsledky z *přejít na soubory* operace pomocí filtru, který 'f':

![C&#43; &#43; přejděte do nabídky](../ide/media/vs2017-go-to-results.png "přejděte do nabídky")

Chcete-li zobrazit seznam filtrech textu, zadejte? následovanými mezerou. Se dá dostat taky **přejít na** příkazů s **upravit** nabídky. Toto je další způsob, jak připomenou hlavní přejít na klávesové zkratky.

![C&#43; &#43; přejděte do nabídky](../ide/media/go-to-menu-cpp.png "přejděte do nabídky")

## <a name="find--find-in-files"></a>Najít / najít v souborech

Hledání textu pro všechno, co můžete spustit ve vašem řešení pomocí **najít (Ctrl + F)** nebo **najít v souborech (Ctrl + Shift + F)** .

Hledání se dají vymezit na výběr, aktuální dokument, všechny otevřené dokumenty, aktuální projekt nebo celé řešení. Můžete použít regulární výrazy, stejně jako prostý text. Také zvýrazní všechny shody automaticky v integrovaném vývojovém prostředí.

![C&#43; &#43; najít](../ide/media/find-cpp.png "najít")

**Najít v souborech** je výkonnější verze **najít** , který zobrazí výsledky v **výsledky hledání** okna. Můžete hledat závislosti externí kód, filtrovat podle typů souborů a další. 

![C&#43; &#43; najít v souborech](../ide/media/find-in-files-cpp.png "najít v souborech")

Můžete uspořádat **najít v souborech** výsledkem dvě okna. Výsledky z více vyhledávání, můžete připojit společně. Klikněte na výsledek, chcete-li přejít do tohoto umístění v souboru.

![C&#43; &#43; najít v souborech](../ide/media/vs2017-find-in-files-results.png "najít v souborech")

Další informace najdete v tématu [najít v souborech](/visualstudio/ide/find-in-files) v dokumentaci k sadě Visual Studio.

## <a name="find-all-references"></a>Najít všechny odkazy

Pokud chcete najít všechny použití symbolu ve vašem základu kódu, umístěte blikající kurzor v nebo bezprostředně po symbolu, pak klikněte pravým tlačítkem na a zvolte **najít všechny odkazy**. Filtrování, řazení nebo seskupení výsledků mnoha různými způsoby. Výsledky naplnit postupně. Jsou klasifikovány jako čte nebo zapisuje do pomoct zjistit, co je v řešení na rozdíl od systémových hlavičkách nebo jiných knihoven.

![C&#43; &#43; najít všechny odkazy](../ide/media/find-all-references-results-cpp.png "najít všechny odkazy")

Seskupení výsledků podle těchto kategorií:

- Projekt a pak definice
- Jenom definice
- Definice a pak projekt
- Definice a pak cesta
- Definice, projekt a pak cesta

 #### <a name="filter-results"></a>Filtrování výsledků

Pro filtrování výsledků, najeďte myší na sloupec a klepněte na ikonu filtrování, která se otevře. Můžete filtrovat výsledky z prvního sloupce, chcete-li skrýt věci jako odkazy na řetězec a komentáře, které nebudete chtít naleznete v tématu.

![C&#43; &#43; najít všechny odkazy na filtry](../ide/media/find-all-references-filters-cpp.png "najít všechny odkazy na filtry")

- **Potvrdit výsledky**: Skutečný kód odkazy na symbol vyhledaly. Například hledání členská funkce volána `Size` vrátí všechny odkazy na `Size` , které odpovídají rozsahu definice třídy `Size`.

- **Nepotvrzený výsledky**: Tento filtr je vypnuto ve výchozím nastavení protože zobrazuje symboly, jejíž název odpovídá ale nejsou skutečné odkazy na symbol, který chcete vyhledat. Například, pokud máte dvě třídy, z nichž každý definuje členskou funkci volat `Size`, a spusťte hledání `Size` na odkaz z objektu `Class1`, všechny odkazy na `Size` z `Class2` zobrazí jako Nepotvrzený.

- **Nezpracované výsledky**: **Najít všechny odkazy** operace může trvat dobu na větší základů kódu, takže v seznamu výsledků se zobrazí "nezpracované" výsledky. Nezpracované výsledky odpovídat názvu symbolu vyhledávaná, ale dosud nebyla potvrzena jako odkazy na skutečný kód. Tento filtr se získat rychlejší výsledky, můžete zapnout. Právě mějte na paměti, že některé výsledky nemusí být skutečný odkazy.

 #### <a name="sort-results"></a>Řazení výsledků

Výsledky můžete řadit podle libovolného sloupce kliknutím na tento sloupec. Můžete přepínat mezi vzestupné nebo sestupné pořadí znovu kliknutím do sloupce.

## <a name="navigation-bar"></a>Navigační panel

Můžete přejít na definici typu v souboru nebo členy, s použitím typu **navigační panel** , který je uveden výše v okně editoru.

![C&#43; &#43; navigační panel](../ide/media/navbar-cpp.png "navigační panel")

## <a name="see-also"></a>Viz také

[Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>
[Upravit a Refaktorovat C++ kódu](read-and-understand-code-cpp.md)</br>
[Spolupráce s živými sdílenou složkou proC++](live-share-cpp.md)
