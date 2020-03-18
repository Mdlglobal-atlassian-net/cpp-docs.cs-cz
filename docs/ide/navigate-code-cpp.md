---
title: Navigace C++ v kódu v aplikaci Visual Studio
description: Pomocí různých nástrojů v aplikaci Visual Studio můžete procházet C++ základ kódu.
ms.date: 05/28/2019
ms.openlocfilehash: 0877fe64e913ab394d9605b9ff0b9825febca793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446736"
---
# <a name="navigate-c-code-in-visual-studio"></a>Navigace C++ v kódu v aplikaci Visual Studio

Sada Visual Studio poskytuje sadu nástrojů, které můžete použít k rychlému a efektivnímu procházení základního kódu.

## <a name="open-an-included-file"></a>Otevřít zahrnutý soubor

Klikněte pravým tlačítkem na direktivu `#include` a vyberte **Přejít k dokumentu**. Nebo vyberte **F12** s kurzorem na této čáře a otevřete soubor.

![&#43; Přejít na možnost nabídky dokument&#43; v dokumentu](../ide/media/go-to-document.png "Přejít k dokumentu")

## <a name="toggle-headercode-file"></a>Přepnout hlavičku/soubor s kódem

Můžete přepínat mezi hlavičkovým souborem a jeho odpovídajícím zdrojovým souborem. Klikněte pravým tlačítkem myši kdekoli v souboru a vyberte možnost **Přepnout hlavičku/soubor s kódem**. Případně můžete vybrat **CTRL + K**, **CTRL + O**.

## <a name="go-to-definitiondeclaration"></a>Přejít k definici nebo deklaraci

Můžete přejít na definici symbolu kódu tak, že na něj kliknete pravým tlačítkem v editoru a vyberete **Přejít k definici**nebo vyberete **F12**. Můžete přejít na deklaraci kliknutím pravým tlačítkem na otevřít místní nabídku nebo výběrem **kombinace kláves CTRL + F12**.

![&&#43; &#43; Přejít k definici](../ide/media/go-to-def.png "Přejít k definici")

## <a name="go-to"></a>Přejít na

**Přejít na** odkazuje na sadu navigačních funkcí, které každý z nich poskytuje konkrétní typ výsledku na základě filtrů, které zadáte. 

Můžete otevřít **Přejít na** pomocí **CTRL +,** . Tato akce vytvoří vyhledávací pole nad dokumentem, který upravujete.

![&#43; &#43; Přejít na](../ide/media/go-to-cpp.png "Přejít na")

**Přejít na** obsahuje tyto filtry hledání:

- **Přejít na řádek** (**CTRL + G**): rychle přejít na jiný řádek v aktuálním dokumentu.
- **Přejít na vše** (**CTRL +,** ) nebo (**CTRL + T**): výsledky hledání zahrnují všechno, co následuje.
- **Přejít k souboru** (**CTRL 1, F**): vyhledejte soubory ve vašem řešení.
- **Přejít na typ** (**CTRL 1, T**): výsledky hledání zahrnují:
  - Třídy, struktury a výčty.
  - Rozhraní a Delegáti (pouze spravovaný kód).
- **Přejít na člena** (**CTRL 1, M**): výsledky hledání zahrnují:
  - Globální proměnné a globální funkce.
  - Členské proměnné třídy a členské funkce.
  - Konstant.
  - Vyčíslení položek
  - Vlastnosti a události.
- **Přejít na symbol** (**CTRL 1, S**): výsledky hledání zahrnují:
  - Výsledky z možnosti přejít na typy a přejít na členy.
  - Všechny zbývající C++ jazykové konstrukce, které obsahují makra.

Když se poprvé vyvoláte, **přejdete na** s **klávesou Ctrl +** , **na vše** se aktivuje (žádné filtry pro výsledky hledání). Pak můžete vybrat požadovaný filtr pomocí tlačítek v blízkosti vyhledávacího pole. Konkrétní filtr můžete vyvolat pomocí odpovídající klávesové zkratky. Tím se otevře vyhledávací pole **Přejít na** s vybraným filtrem. Všechny klávesové zkratky lze konfigurovat.

Chcete-li použít textový filtr, spusťte vyhledávací dotaz s odpovídajícím znakem filtru následovaným mezerou. (**Přejít na řádek** může volitelně vynechat místo.) K dispozici jsou tyto textové filtry:

- Přejít na vše: (žádný textový filtr)
- Přejít na číslo řádku::
- Přejít k souboru: f
- Přejít na typ: t
- Přejít ke členu: m
- Přejít na symbol: #

Následující příklad ukazuje výsledky z operace *Přejít k souborům* pomocí filtru "f":

![&#43; &#43; V nabídce Přejít na](../ide/media/vs2017-go-to-results.png "Přejít na nabídku")

Seznam textových filtrů zobrazíte tak, že zadáte a? následováno mezerou. Přístup k příkazům **Přejít na** můžete také získat pomocí nabídky **Upravit** . To je jiný způsob, jak připomenout hlavní **Přejít k** klávesovým zkratkám.

![&#43; &#43; V nabídce Přejít na](../ide/media/go-to-menu-cpp.png "Přejít na nabídku")

## <a name="find-or-find-in-files"></a>Najít nebo najít v souborech

Můžete spustit hledání libovolného textu ve vašem řešení pomocí **find** (**CTRL + F**) nebo **najít v souborech** (**CTRL + SHIFT + f**).

**Hledání** může být vymezeno na výběr, aktuální dokument, všechny otevřené dokumenty, aktuální projekt nebo celé řešení. Můžete použít regulární výrazy a prostý text. Také zvýrazní všechny shody automaticky v integrovaném vývojovém prostředí.

![Hledání&#43; &#43; v jazyce C](../ide/media/find-cpp.png "Hledání")

**Hledání v souborech** je výkonnější verze **hledání** , která v okně **výsledky hledání** zobrazuje výsledky. Můžete hledat externí závislosti v kódu, filtrovat podle typů souborů a další. 

![&#43; &#43;](../ide/media/find-in-files-cpp.png "Najít v souborech")

Výsledky **hledání v souborech** můžete uspořádat ve dvou oknech. Můžete přidat výsledky z několika hledání najednou. Vyberte výsledek, který chcete přejít do tohoto umístění v souboru.

![&#43; &#43;](../ide/media/vs2017-find-in-files-results.png "Najít v souborech")

Další informace najdete v tématu [hledání v souborech](/visualstudio/ide/find-in-files) v dokumentaci k sadě Visual Studio.

## <a name="find-all-references"></a>Najít všechny odkazy

Chcete-li najít všechna použití symbolu v základu kódu, umístěte blikající kurzor do nebo hned za symbol, klikněte pravým tlačítkem myši a vyberte možnost **Najít všechny odkazy**. Výsledky můžete filtrovat, řadit nebo seskupovat mnoha různými způsoby. Výsledky jsou přírůstkově naplněny. Jsou klasifikované jako čtení nebo zápisy, které vám pomůžou zjistit, co je ve vašem řešení, na rozdíl od systémových hlaviček nebo jiných knihoven.

![&#43; &#43;](../ide/media/find-all-references-results-cpp.png "Najít všechny odkazy")

Výsledky můžete seskupit podle následujících kategorií:

- Projekt a pak definice
- Jenom definice
- Definice a pak projekt
- Definice a pak cesta
- Definice, projekt a pak cesta

#### <a name="filter-results"></a>Filtrování výsledků

Pokud chcete filtrovat výsledky, najeďte myší na sloupec a vyberte ikonu filtrování, která se zobrazí. Můžete filtrovat výsledky z prvního sloupce a skrýt tak například řetězce a odkazy na komentáře, které nechcete, aby bylo možné je zobrazit.

![&#43; Vyhledá všechny filtry&#43; odkazů.](../ide/media/find-all-references-filters-cpp.png "Najít všechny odkazy na filtry")

- **Potvrzené výsledky**: skutečný kód odkazuje na hledaný symbol. Například vyhledávání členské funkce nazvané `Size` vrátí všechny odkazy na `Size`, které odpovídají oboru třídy definující `Size`.

- **Nepotvrzené výsledky**: Tento filtr je ve výchozím nastavení vypnutý, protože zobrazuje symboly, jejichž název odpovídá, ale nejedná se o skutečné odkazy na symbol, který hledáte. Například pokud máte dvě třídy, které každý definují členskou funkci nazvanou `Size`a spustíte hledání `Size` na odkaz z objektu `Class1`, všechny odkazy na `Size` z `Class2` se zobrazí jako nepotvrzené.

- **Nezpracované výsledky**: u větších základů kódu můžou operace **Najít všechny odkazy** trvat delší dobu, takže v seznamu výsledků se tady zobrazí "nezpracované" výsledky. Nezpracované výsledky se shodují s názvem hledaného symbolu, ale ještě nebyl potvrzen jako skutečný odkaz na kód. Tento filtr můžete zapnout, chcete-li dosáhnout rychlejších výsledků. Stačí vědět, že některé výsledky nemusí být skutečné odkazy.

#### <a name="sort-results"></a>Řazení výsledků

Výběrem tohoto sloupce můžete seřadit výsledky podle libovolného sloupce. Sloupec můžete přepínat vzestupně nebo sestupně, a to tak, že ho vyberete znovu.

## <a name="navigation-bar"></a>Navigační panel

Můžete přejít k definici typu v souboru nebo zadat členy pomocí **navigačního panelu** , který je nad oknem editoru.

![Navigační&#43; &#43; panel jazyka C](../ide/media/navbar-cpp.png "Navigační panel")

## <a name="see-also"></a>Viz také

- [Čtení a pochopení C++ kódu](read-and-understand-code-cpp.md)</br>
- [Upravit a Refaktorovat C++ kód](read-and-understand-code-cpp.md)</br>
- [Spolupráce s Live Share proC++](live-share-cpp.md)
