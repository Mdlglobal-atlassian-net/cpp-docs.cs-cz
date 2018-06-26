---
title: HTML – základy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c4ebbc8e792e36461f7c52c17fa23815239e323
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929087"
---
# <a name="html-basics"></a>HTML – základy
Většina prohlížečů mají možnost kontroly zdrojový kód HTML stránky, které budete procházet. Při zobrazení zdroje, zobrazí se počet značek HTML (jazyk) uzavřeny v lomené závorky (<>), spolu s textem.  
  
 Následující postup použijte k vytvoření jednoduché webové stránky značky HTML. V těchto krocích budete zadejte ve formátu prostého textu do souborů v programu Poznámkový blok, provést několik změn, uložte soubor a znovu načíst stránku v prohlížeči zobrazit změny.  
  
#### <a name="to-create-an-html-file"></a>Chcete-li vytvořit soubor HTML  
  
1.  Otevřete Poznámkový blok nebo v editoru prostý text.  
  
2.  Z **soubor** nabídce zvolte **nový**.  
  
3.  Zadejte následující řádky:  
  
 ```  
 <HTML>  
 <HEAD>  
 <TITLE>Top HTML Tags</TITLE>  
 </HEAD>  
 </HTML>  
 ```  
  
4.  Z **soubor** nabídce zvolte **Uložit**a uložte soubor jako c:\webpages\First.htm. Nechte soubor otevřený v editoru.  
  
5.  Přepněte do prohlížeče a z **soubor** nabídce zvolte **otevřete**, nebo typ *file://C:/webpages/first.htm* do textového pole adresy URL v prohlížeči. Měli byste vidět prázdná stránka s titulek okno "Hlavní značky HTML."  
  
     Všimněte si značky jsou spárovat a jsou zahrnuty v lomených závorkách. Značky nejsou malá a velká písmena, ale malá a velká písmena se často používá k zajištění značky zvýraznění.  
  
     Značky \<HTML > spustí dokumentu a značky  \< /HTML > ho ukončí. Koncové značky (ne vždy vyžadován) jsou stejné jako počáteční značka, ale mají lomítkem (/) před značky. Měla by existovat žádné mezery mezi ostré závorky (<) a spusťte vaše značky.  
  
6.  Přepněte zpět do poznámkového bloku a po  \< /HEAD > řádek, zadejte:  
  
 ```  
 <BODY>  
    HTML is swell.  
    Life is good.  
 </BODY>  
 ```  
  
7.  Z **soubor** nabídce zvolte **Uložit**.  
  
8.  Přepněte zpět na prohlížeči a aktualizujte stránku.  
  
     Slova se zobrazí v oblasti klienta okna prohlížeče. Všimněte si, že vaše návrat je ignorován. Pokud chcete mít koncem řádku, musíte zahrnout `<BR>` značka po první řádek.  
  
     Pro všechny kroky, které řídí, zadejte text kdekoli mezi \<textu > a  \< /BODY > Chcete-li přidat k tělu dokumentu.  
  
9. Přidáte hlavičku:  
  
 ```  
 <H3>Here's the big picture</H3>  
 ```  
  
10. Přidejte bitovou kopii, pomocí .gif soubor uložený ve stejném adresáři jako stránku:  
  
 ```  
 <IMG src="yourfile.gif">  
 ```  
  
11. Přidejte seznamu:  
  
 ```  
 <UL>Make me an unordered list.  
 <LI>One programmer</LI>  
 <LI>Ten SDKs</LI>  
 <LI>Great Internet Apps</LI>  
 </UL>  
 ```  
  
12. Místo toho číslo seznamu, použijte spárovat \<OL > a \</OL > značky místě \<UL > a \</UL > značky.  
  
 Které by vám pomůžou začít. Pokud se zobrazí skvělé funkce na webové stránce, můžete zjistit jak byl vytvořen tak, že prověří zdroji HTML. Editorů jazyka HTML, jako je například Microsoft titulní stránky lze použít k vytvoření jednoduché i rozšířené stránky.  
  
 Tady je celý zdrojový HTML pro soubor, který jste si vytváření:  
  
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
  
 Úplný popis značky, atributy a rozšíření najdete v části specifikace Hypertext Markup Language (HTML):  
  
 [http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)  
  
## <a name="see-also"></a>Viz také  
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

