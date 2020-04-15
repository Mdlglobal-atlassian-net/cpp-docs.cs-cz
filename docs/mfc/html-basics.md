---
title: HTML – základy
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377251"
---
# <a name="html-basics"></a>HTML – základy

Většina prohlížečů má možnost zkoumat zdroj HTML stránek, které procházíte. Při zobrazení zdroje se zobrazí řada značek HTML (html markup language), obklopených úhlovými závorkami (<>), proloženými textem.

Následující kroky používají značky HTML k vytvoření jednoduché webové stránky. V těchto krocích zadáte prostý text do souboru v poznámkovém bloku, provedete několik změn, uložíte soubor a znovu načtete stránku do prohlížeče, abyste viděli změny.

#### <a name="to-create-an-html-file"></a>Vytvoření souboru HTML

1. Otevřete poznámkový blok nebo libovolný editor ve formátu prostého textu.

1. V nabídce **Soubor** zvolte **Nový**.

1. Zadejte následující řádky:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Z nabídky **Soubor** zvolte **Uložit**a uložte soubor jako c:\webpages\First.htm. Ponechejte soubor otevřený v editoru.

1. Přepněte do prohlížeče a z nabídky **Soubor** zvolte **Otevřít**nebo zadejte *file://C:/webpages/first.htm* do textového pole url prohlížeče. Měla by se zobrazit prázdná stránka s titulkem okna "Top HTML Tags".

   Všimněte si, že značky jsou spárovány a jsou zahrnuty v úhlových závorkách. Značky nerozlišují malá a velká písmena, ale velká písmena se často používají k tomu, aby značky vynikly.

   > \<html tagu spustí dokument \<a značka /HTML> ho ukončí. Koncové značky (ne vždy povinné) jsou stejné jako počáteční značka, ale mají před ní lomítko (/). Mezi úhlovou závorkou (<) a začátkem značky by neměly být žádné mezery.

1. Přepněte zpět do poznámkového \<bloku a za řádek /HEAD> zadejte:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Z nabídky **Soubor** zvolte **Uložit**.

1. Přepněte zpět do prohlížeče a aktualizujte stránku.

   Slova se zobrazí v klientské oblasti okna prohlížeče. Všimněte si, že vaše návrat vozíku je ignorována. Pokud chcete mít zalomení řádku, `<BR>` musíte za první řádek zahrnout značku.

   Pro všechny následující kroky vložte text \<kdekoli \<mezi BODY> a /BODY> přidat do těla dokumentu.

1. Přidání záhlaví:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Přidejte obrázek pomocí souboru GIF uloženého ve stejném adresáři jako na stránce:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Přidat seznam:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Chcete-li místo toho \<očíslovat seznam, použijte místo \<značek \<UL> a /UL>> spárované značky OL> a \</OL.

To by tě mělo nastartovat. Pokud se na webové stránce zobrazí skvělá funkce, můžete zjistit, jak byla vytvořena, a to tak, že prozkoumáte zdroj HTML. Editory HTML, jako je microsoft frontpage, lze použít k vytvoření jednoduchých i pokročilých stránek.

Zde je celý zdroj HTML pro soubor, který jste vytvářeli:

```html
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

Úplný popis značek, atributů a rozšíření naleznete ve specifikaci html (Hypertext Markup Language):

[Poslední publikovaná verze HTML](https://www.w3.org/TR/html/) na W3C.org.

## <a name="see-also"></a>Viz také

[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)
