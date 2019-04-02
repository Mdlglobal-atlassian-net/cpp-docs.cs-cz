---
title: 'TN040: Knihovny MFC-OLE místní změny velikosti a měřítka'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: c2cb25388184ac969bec7c01d8077a458c03a03a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775280"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: MFC/OLE – místní změny velikosti a měřítka

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje problémy týkající se úpravy na místě a jak server provádět správné změna měřítka zobrazení a změna velikosti na místě. Aktivace na místě WYSIWYG koncept je provést ještě o krok v tomto kontejnery a servery vzájemně spolupracovat a zejména interpretovat specifikaci OLE téměř stejným způsobem.

Z důvodu zavřít interakce mezi kontejnerem a podporuje místní aktivace server existuje několik očekávání od koncového uživatele, který by se měl zachovat:

- Zobrazení prezentace (metasoubor vykreslen v `COleServerItem::OnDraw` přepsání) by měl vypadat stejně, jako když je vykreslen pro úpravy (s tím rozdílem, že nástroje pro úpravy se nezobrazí).

- Když zvětší nebo zmenší kontejneru, v okně server by měl taky!

- Kontejner a server by měl zobrazit objekty s možností úprav pomocí stejné metriky. To znamená, že používá režim mapování na základě počtu *logické* pixely na palec – ne fyzických pixely na palec, při vykreslování na zobrazovací zařízení.

> [!NOTE]
>  Protože aktivace na místě platí jenom pro položky, které jsou vloženy (nepřipojené), změna měřítka zobrazení vztahuje pouze na vložené objekty. Zobrazí se rozhraní API v obou `COleServerDoc` a `COleServerItem` , která se používají pro přiblížení. Důvod pro tento dichotomy je, že pouze funkce, které jsou platné pro propojené a vložené položky jsou ve `COleServerItem` (díky tomu můžete mít běžnou implementaci) a funkce, které jsou platné pouze pro vložené objekty jsou umístěny v `COleServerDoc` třídy (z perspektivy serveru, je **dokumentu** který je vložený).

Většinu zatížení se přikládá implementátora server, musí server mějte na faktor zvětšování kontejneru a jeho úpravy rozhraní podle potřeby upravit. Ale jak server určit na faktor zvětšování, která používá kontejneru

## <a name="mfc-support-for-zooming"></a>Podpora MFC pro přiblížení

Aktuální lupy se dají určit pomocí volání `COleServerDoc::GetZoomFactor`. Toto volání při dokument není aktivní místní vždy způsobí faktor zvětšení na 100 % (nebo poměr 1:1). Volání při místní aktivní může vracely něco jiného než 100 %.

Změna měřítka zobrazení správně příklad najdete v ukázce MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Přiblížit HIERSVR ztěžuje skutečnost, že se zobrazí text a text, většinou nejsou adekvátní lineárně (pomocných parametrů, typografických zásad daného, návrh šířky a výšky všech zkomplikovat věci). Stále, HIERSVR přiměřené odkaz pro implementaci správně přibližování a tak je kurzu MFC [SCRIBBLE](../overview/visual-cpp-samples.md) (krok 7).

`COleServerDoc::GetZoomFactor` Určuje, na faktor zvětšování založené na celé řadě různých metrik dostupných z kontejneru nebo z provádění vaší `COleServerItem` a `COleServerDoc` třídy. Stručně řečeno aktuální faktor zvětšování závisí na následující vzorec:

```
Position Rectangle (PR) / Container Extent (CE)
```

POZICI obdélníku je určen kontejner. Je vrácen do serveru během místní aktivace při `COleClientItem::OnGetItemPosition` nazývá a aktualizuje, když kontejner volá na server `COleServerDoc::OnSetItemRects` (voláním `COleClientItem::SetItemRects`).

ROZSAH KONTEJNERU je o něco složitější k výpočtu. Pokud kontejner má název `COleServerItem::OnSetExtent` (voláním `COleClientItem::SetExtent`), pak rozsah KONTEJNERU, je tato hodnota převedena na pixelech na základě počtu pixelů na logický palec. Pokud kontejner nevolala SetExtent (což obvykle platí), je v rozsahu KONTEJNERU velikostí vrácenou z `COleServerItem::OnGetExtent`. Tedy pokud kontejneru nebyla volána SetExtent, rozhraní předpokládá, že pokud udělal kontejneru by mít volány ho se 100 % přirozené rozsahu (hodnota vrácená z `COleServerItem::GetExtent`). Uvádí další způsob rozhraní se předpokládá, že je kontejner zobrazení 100 % (menší častěji, ne) položky.

Je důležité si uvědomit, že i když `COleServerItem::OnSetExtent` a `COleServerItem::OnGetExtent` podobně jako názvy jejich není manipulovat s stejný atribut položky. `OnSetExtent` volá se, že nechat server vědět, jak velká část objektu je viditelný v kontejneru (bez ohledu na faktor zvětšování) a `OnGetExtent` volá se kontejnerem, chcete-li zjistit ideální velikost objektu.

Zobrazením všech zapojených rozhraní API, můžete získat dostáváme postupně jasnější představu:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Tato funkce by měl vrátit "fyzická velikost" v jednotkách HIMETRIC položky. Nejlepší způsob, jak si můžete představit "fyzická velikost" je definovat jako velikost, kterou může zobrazit při tisku. Velikostí vrácenou zde je konstantní pro konkrétní položku obsahu (podobně jako tento metasoubor, což je konstantní pro určité položky). Tato velikost se nemění, při zvětšování u položky. Obvykle nezmění při kontejneru poskytuje položka větší nebo menší prostor voláním `OnSetExtent`. Příklad změny může být u jednoduchý textový editor se žádné "margin" schopnost, která zalomeného textu podle poslední rozsahu odesílaných kontejneru. Pokud změníte server, server pravděpodobně nastaven OLEMISC_RECOMPOSEONRESIZE bit v systémovém registru (viz dokumentace ke službě OLE SDK pro další informace o této možnosti).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Tato funkce je volána, když kontejner se zobrazí "víc nebo míň" objektu. Většina kontejnery nebude volat to vůbec. Výchozí implementace ukládá poslední hodnotu získanou z kontejneru v "m_sizeExtent", který se používá v `COleServerDoc::GetZoomFactor` při výpočtu hodnoty rozsahu KONTEJNERU je popsáno výše.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Tato funkce je volána, pouze v případě, že je místní aktivní dokument. Je volána při aktualizaci kontejneru umístění nebo ořezové použitý pro položku. POZICI obdélníku, jak je popsáno výše, poskytuje čítač pro výpočet faktoru zvětšení. Server můžete požádat o změnu umístění položky voláním `COleServerDoc::RequestPositionChange`. Kontejner může nebo nemusí reagovat na tento požadavek voláním `OnSetItemRects` (voláním `COleServerItem::SetItemRects`).

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

Je důležité si uvědomit, že tento metasoubor vytvořené přepsání `COleServerItem::OnDraw` vytváří přesně stejné metasoubor, bez ohledu na aktuální faktor zvětšování. Kontejner se bude škálovat metasoubor podle potřeby. To je zásadní rozdíl mezi zobrazení `OnDraw` a položka serveru `OnDraw`. Zobrazit úchyty změna měřítka zobrazení, položky pouze vytvoří *roztahováním* metasoubor a zůstane až do kontejneru provedete příslušné měřítka.

Nejlepší způsob, jak zajistit správné chování serveru je použít implementaci `COleServerDoc::GetZoomFactor` Pokud váš dokument je na místě aktivní.

## <a name="mfc-support-for-in-place-resizing"></a>Podpora MFC pro změnu velikosti na místě

MFC plně implementuje rozhraní místní změny velikosti, jak je popsáno ve specifikaci OLE 2. Uživatelské rozhraní je podporován `COleResizeBar` třídy, vlastní zprávu WM_SIZECHILD a zvláštní zpracování této zprávy v `COleIPFrameWnd`.

Můžete provádět různé zpracování této zprávy, než je zadán v rámci rozhraní. Jak je popsáno výše, rozhraní ponechá místní změny velikosti až kontejneru výsledky – server reaguje na změnu v hodnotě na faktor zvětšování. Pokud kontejneru jsou reaguje obě nastavením rozsahu KONTEJNERU a POZICI obdélníku během zpracování jeho `COleClientItem::OnChangeItemPosition` (volá se v důsledku volání `COleServerDoc::RequestPositionChange`) poté způsobí změnu velikosti na místě zobrazující "víc nebo míň" položky v úpravy okno. Pokud jsou reaguje kontejneru tak, že právě POZICI obdélníku nastavíte během zpracování `COleClientItem::OnChangeItemPosition`, se změní na faktor zvětšování a položka se zobrazí "možnosti zvětšit nebo zmenšit."

Server můžete řídit (do určité míry), co se stane, že během tohoto vyjednávání. Tabulky, například může rozhodnout, jestli chcete zobrazit více nebo méně buněk, když uživatel změní velikost okna při úpravách položky místní. Textových procesorů může rozhodnout, jestli chcete-li změnit okraje stránky"", jsou stejné jako v okně a balit text nové rozpětí. Servery implementovat to tak, že změníte přirozené rozsahu (velikostí vrácenou z `COleServerItem::OnGetExtent`) po dokončení změny velikosti. To způsobí POZICI obdélníku a kontejner rozsah, změnit stejným způsobem, výsledkem je na stejné faktor zvětšování, ale větší nebo menší oblasti zobrazení. Kromě toho, víc nebo míň dokumentu se nebude zobrazovat v metasoubor generovaných `OnDraw`. V takovém případě samotný dokument se mění, když uživatel změní položka, namísto pouze oblasti zobrazení.

Můžete implementovat vlastní změny velikosti a využít uživatelské rozhraní poskytované `COleResizeBar` tak, že přepíšete WM_SIZECHILD zprávu ve vašich `COleIPFrameWnd` třídy. Další informace na konkrétních podrobnostech WM_SIZECHILD najdete v tématu [Technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
