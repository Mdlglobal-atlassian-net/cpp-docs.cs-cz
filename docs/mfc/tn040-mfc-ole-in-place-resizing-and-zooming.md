---
title: 'TN040: MFC OLE na místě změny velikosti a měřítka | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dbd817e6bcb9c7ff526bef98bd5c2c8c1f1bb3e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955167"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: změny velikosti a měřítka na místě v prostředích MFC/OLE
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka se popisují problémy, týkající se úpravy na místě a jak server by měl provést správné přibližování a změna velikosti na místě. Aktivace na místě WYSIWYG koncept se ještě o krok napřed v tomto kontejnery a servery vzájemně spolupracovat a na konkrétní interpretovat specifikace OLE prakticky stejně.  
  
 Z důvodu zavřít interakce mezi kontejneru a serveru podporu aktivace na místě jsou počet očekávání z koncového uživatele, který by se měl zachovat:  
  
-   Zobrazení prezentace (metafile vykresluje v `COleServerItem::OnDraw` přepsat) by měla vypadat přesně stejný jako při kreslení pro úpravy (kromě toho, že nejsou viditelné nástroje pro úpravy).  
  
-   Když kontejneru zvětší, by měl příliš okno serveru!  
  
-   Kontejner i server by měl zobrazit objekty pro úpravy pomocí stejné metriky. To znamená, že pomocí mapování režimu založeném na počet *logické* počet pixelů na palec – ne fyzických počet pixelů na palec, při vykreslování do zobrazení zařízení.  
  
> [!NOTE]
>  Protože aktivace na místě platí jenom pro položky, které jsou vloženy (není propojené), přibližování platí pouze pro vložené objekty. Zobrazí se rozhraní API v obou `COleServerDoc` a `COleServerItem` , který se používá pro přiblížení a oddálení. Důvod této dichotomy je, že jenom funkce, které jsou platné pro propojené a vložené položky jsou `COleServerItem` (můžete tak mít běžných implementací) a funkce, které jsou platné pouze pro vložené objekty jsou umístěné v `COleServerDoc` třídy (z perspektivy serveru, je **dokumentu** který vložené).  
  
 Většinu zatížení je umístěn na serveru implementátor, v, že server musí mít přehled o faktor zvětšování kontejneru a jeho úpravy rozhraní podle potřeby upravit. Ale jak server určí na faktor zvětšování, který používá kontejneru  
  
## <a name="mfc-support-for-zooming"></a>Podpora MFC pro přiblížení a oddálení  
 Aktuální faktor zvětšování se dá určit pomocí volání `COleServerDoc::GetZoomFactor`. Toto volání při dokument není aktivní na místě vždy výsledkem bude Multi-Factor 100 % zvětšení (nebo poměr 1:1). Volání ho, když místní active může vrátit něco jiného než 100 %.  
  
 K zobrazení příkladu správně přibližování najdete v části ukázka MFC OLE [HIERSVR](../visual-cpp-samples.md). Přiblížení a oddálení v HIERSVR ztěžuje skutečnost, že se zobrazí text a text, obecně není vhodné lineárně (pomocné parametry, typografických zásad, návrh šířky a výšky všechny zkomplikovat věci). Přesto HIERSVR je přiměřené odkaz pro implementaci přibližování správně, a stejně tak kurzu MFC [KLIKYHÁKY](../visual-cpp-samples.md) (krok 7).  
  
 `COleServerDoc::GetZoomFactor` Určuje, na faktor zvětšování na základě počtu jiné metriky dostupné z kontejneru nebo z implementace vaše `COleServerItem` a `COleServerDoc` třídy. Stručně řečeno aktuální faktor zvětšování je dáno následující vzorec:  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 POZICE RÁMEČKU je určen podle kontejneru. Je vrácen do serveru během aktivace na místě při `COleClientItem::OnGetItemPosition` se označuje jako a bude aktualizován, jakmile kontejneru volá serveru `COleServerDoc::OnSetItemRects` (pomocí volání `COleClientItem::SetItemRects`).  
  
 ROZSAH KONTEJNERU, je trochu složitější k výpočtu. Pokud je volána kontejneru `COleServerItem::OnSetExtent` (pomocí volání `COleClientItem::SetExtent`), pak rozsah KONTEJNERU, je tato hodnota převést na pixelů na základě počtu pixelů na logický palec. Pokud kontejneru nebyla zavolána SetExtent (což se obvykle stává), pak v KONTEJNERU rozsahu je velikost vrácená z `COleServerItem::OnGetExtent`. Ano, pokud kontejneru nebyla volána SetExtent, rozhraní předpokládá, že pokud to kontejneru by mít volány ho s 100 % přirozené rozsah (hodnota vrácená z `COleServerItem::GetExtent`). Uvádí další způsob, rozhraní se předpokládá, že kontejner zobrazuje 100 % (ne více, ani méně) položky.  
  
 Je důležité si uvědomit, že i když `COleServerItem::OnSetExtent` a `COleServerItem::OnGetExtent` mají podobné názvy, není jejich zpracování stejný atribut položky. `OnSetExtent` je volána umožníte serveru vědět, kolik objektu je viditelný v kontejneru (bez ohledu na faktor zvětšování) a `OnGetExtent` volá kontejneru ideální velikost objektu.  
  
 Pohledem na každé rozhraní API související se situací, můžete získat lepší přehled:  
  
## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent  
 Tato funkce by měl vrátit "přirozené velikost" v jednotkách HIMETRIC položky. Nejlepší způsob, jak si můžete představit "přirozené velikost" je definována jako velikost, může se objevit při tisku. Velikost vrátil tady je konstantní pro konkrétní položky obsah, (podobně jako metafile, což je konstantní určité položky). Tato velikost nezmění při změně měřítka k položce. Obvykle nemění při kontejneru poskytuje položku více nebo méně místa voláním `OnSetExtent`. Příkladem změnu může být u jednoduchý textový editor se žádné "sazba" funkci, která zalomeného textu podle poslední rozsah poslal kontejneru. Pokud se změní server, server pravděpodobně nastavuje OLEMISC_RECOMPOSEONRESIZE bit v registru systému (viz dokumentace k sadě OLE SDK pro další informace na tuto možnost).  
  
## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent  
 Tato funkce je volána, když kontejneru ukazuje "vyšší nebo nižší" objektu. Většina kontejnery nebude volat to vůbec. Výchozí implementace ukládá poslední hodnotu přijaté z kontejneru v 'm_sizeExtent', který je používán `COleServerDoc::GetZoomFactor` při výpočtu hodnota rozsahu KONTEJNERU popsané výše.  
  
## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Tato funkce je volána, pouze v případě, že dokument je aktivní na místě. Je volána při kontejneru aktualizuje umístění nebo výstřižek použitý pro položku. POZICE RÁMEČKU, jak je popsáno výše, poskytuje čítači pro výpočet faktoru zvětšení. Server můžete požádat o změnit umístění položky voláním `COleServerDoc::RequestPositionChange`. Kontejner může nebo nemusí reagovat na tento požadavek voláním `OnSetItemRects` (pomocí volání `COleServerItem::SetItemRects`).  
  
## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw  
 Je důležité si uvědomit, vytvořený metafile přepsáním z `COleServerItem::OnDraw` vytváří přesně stejnou metafile, bez ohledu na aktuální faktor zvětšování. Kontejner bude škálovat metafile podle potřeby. To je zásadní rozdíl mezi zobrazení `OnDraw` a položku serveru `OnDraw`. Obslužné rutiny zobrazení měřítka, položka právě vytvoří *umožňujícím* metafile a zůstane až do kontejneru provedete příslušné měřítka.  
  
 Nejlepší způsob zajistit, že váš server chovat správně, je použít implementaci `COleServerDoc::GetZoomFactor` Pokud je na místě aktivní dokument.  
  
## <a name="mfc-support-for-in-place-resizing"></a>Podpora MFC pro změnu velikosti na místě  
 MFC plně implementuje rozhraní změny velikosti na místě, jak je popsáno v specifikace OLE 2. Podporuje uživatelské rozhraní `COleResizeBar` třídy, vlastní zprávu WM_SIZECHILD a zvláštní zpracování této zprávy v `COleIPFrameWnd`.  
  
 Můžete implementovat jiný zpracování této zprávy, než je zadán pomocí rozhraní. Jak je popsáno výše, rozhraní opustí výsledky až kontejneru Změna velikosti na místě – server odpoví na změnu v hodnotě na faktor zvětšování. Pokud kontejner reaguje obou nastavením rozsah KONTEJNERU a pozice RÁMEČKU během zpracování jeho `COleClientItem::OnChangeItemPosition` (volat v důsledku volání `COleServerDoc::RequestPositionChange`) a změny velikosti na místě bude mít za následek zobrazující "vyšší nebo nižší" položky v úprav okno. Pokud kontejner reaguje pouze během zpracování pomocí nastavení RÁMEČEK pozice `COleClientItem::OnChangeItemPosition`, se změní na faktor zvětšování a položka se zobrazí "možnosti příchozí nebo odchozí."  
  
 Server můžete řídit (do určité míry), co se stane, že během tohoto vyjednávání. Tabulky, například může zvolit, zda zobrazit více nebo méně buněk, když uživatel změní velikost okna při úpravách položky místní. Textových procesorů může zvolit, zda změnit okraje stránky"", jsou stejná jako okna a text zalomit do nového okraje. Servery tuto funkci implementovat změnou přirozené rozsah (velikost vrácená z `COleServerItem::OnGetExtent`) po dokončení změny velikosti. To způsobí RÁMEČEK pozice a kontejner rozsah, změnit tak, že stejnou úroveň, výsledkem je na stejné faktor zvětšování, ale větší nebo menší zobrazení oblasti. Kromě toho, vyšší nebo nižší dokumentu se nebude zobrazovat v metafile generované `OnDraw`. V takovém případě samotného dokumentu mění, když uživatel změní velikost položky, namísto právě oblasti zobrazení.  
  
 Můžete implementovat vlastní změny velikosti a využít uživatelské rozhraní služby `COleResizeBar` přepsáním WM_SIZECHILD zprávu ve vaší `COleIPFrameWnd` třídy. Další informace o specifikacích WM_SIZECHILD najdete v tématu [Technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

