---
title: HTML – základy
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 63a866786abc3b1eaa87a06492b43b1c9e354882
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278382"
---
# <a name="html-basics"></a>HTML – základy

Většina prohlížečů schopné zkoumání zdrojový kód HTML stránky, které můžete procházet. Při zobrazení zdroje se zobrazí počet značek HTML (DHTML) ohraničen ostrými závorkami (<>), spolu s textem.

Následující postup použijte k vytvoření jednoduché webové stránky značky HTML. V následujícím postupu budete zadejte ve formátu prostého textu do souboru v programu Poznámkový blok, provést několik změn, uložte soubor a znovu načíst stránku v prohlížeči pro zobrazení vašich změn.

#### <a name="to-create-an-html-file"></a>Chcete-li vytvořit soubor HTML

1. Otevřete Poznámkový blok nebo libovolný textový editor.

1. Z **souboru** nabídce zvolte **nový**.

1. Zadejte následující řádky:

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. Z **souboru** nabídce zvolte **Uložit**a uložte soubor jako c:\webpages\First.htm. Nechte soubor otevřený v editoru.

1. Přepněte do prohlížeče a z **souboru** nabídce zvolte **otevřít**, nebo typ *file://C:/webpages/first.htm* textového pole URL v prohlížeči. Zobrazí se prázdná stránka s titulek okna "Hlavní značky HTML."

   Všimněte si, že značky jsou párovány a jsou zahrnuty v lomených závorkách. Slovech se nerozlišují malá a velká písmena, ale malá a velká písmena se často používá značek zvýraznění.

   Značka \<HTML > spustí dokumentu a značky  \< /HTML > neukončí. Koncové značky (není vždy nutné) jsou stejné jako počáteční značku, ale mají lomítkem (/) před značku. Měla by existovat žádné mezery mezi ostré závorky (<) a spusťte vaši značku.

1. Přepněte zpět do poznámkového bloku a po  \< /HEAD > řádek, zadejte:

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. Z **souboru** nabídce zvolte **Uložit**.

1. Přepněte zpět do prohlížeče a aktualizujte stránku.

   Slova se zobrazí v klientské oblasti okna prohlížeče. Všimněte si, že vaše zalomení řádku je ignorován. Pokud chcete mít konce řádku, je nutné zahrnout `<BR>` značky po první řádek.

   Pro všechny kroky, které řídí, vložit text kdekoli mezi \<text > a  \< /BODY > Chcete-li přidat do těla dokumentu.

9. Přidáte záhlaví:

```
<H3>Here's the big picture</H3>
```

10. Přidání obrázku, pomocí souborů .gif uloženy ve stejném adresáři jako stránka:

```
<IMG src="yourfile.gif">
```

11. Přidání seznamu:

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. Místo toho čísel v seznamu, použijte spárované \<OL > a \</OL > značky místo \<UL > a \</UL > značky.

Který by vám pomůžou začít. Pokud se na webové stránce skvělé funkce, můžete zjistit jak byl vytvořen prozkoumáním zdrojový kód HTML. Editorů jazyka HTML, jako je přední stránce společnosti Microsoft lze použít k vytvoření jednoduché i pokročilé stránky.

Tady je celý zdrojový kód HTML soubor, který jsme vám sestavení:

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Úplný popis značek, atributy a rozšíření naleznete ve specifikaci Hypertext Markup Language (HTML):

[Nejnovější publikované verzi HTML](https://www.w3.org/TR/html/) na W3C.org.

## <a name="see-also"></a>Viz také:

[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)
