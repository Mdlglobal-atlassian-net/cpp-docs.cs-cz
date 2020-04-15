---
title: 'TN040: Změna velikosti a přiblížení knihovny MFC-OLE na místě'
ms.date: 11/04/2016
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: 65f9ef04c9740e8e6f0a8e72d9d6c39008198755
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372157"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: změny velikosti a měřítka na místě v prostředích MFC/OLE

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka se bude zabývat otázkami týkajícími se úprav na místě a jak by měl server dosáhnout správného přiblížení a změna velikosti na místě. S aktivací na místě wysiwyg koncept je přijata o krok dále v tom kontejnery a servery vzájemně spolupracují a zejména interpretovat specifikace OLE v podstatě stejným způsobem.

Z důvodu úzké interakce mezi kontejnerem a serverem podporující aktivaci na místě existuje řada očekávání od koncového uživatele, který by měl být zachován:

- Zobrazení prezentace (metasoubor nakreslený v `COleServerItem::OnDraw` přepsání) by mělo vypadat přesně stejně jako při kreslení pro úpravy (s tím rozdílem, že nástroje pro úpravy nejsou viditelné).

- Když se kontejner přiblíží, okno serveru by mělo také!

- Kontejner i server by měly zobrazit objekty pro úpravy pomocí stejných metrik. To znamená použití režimu mapování na základě počtu *logických* obrazových bodů na palec – nikoli fyzických obrazových bodů na palec, při vykreslování na zobrazovacím zařízení.

> [!NOTE]
> Vzhledem k tomu, že aktivace na místě se vztahuje pouze na položky, které jsou vložené (nepropojené), přiblížení se vztahuje pouze na vložené objekty. Zobrazí se api v `COleServerDoc` `COleServerItem` obou a které se používají pro přiblížení. Důvodem pro tuto dichotomii je, že pouze funkce, které `COleServerItem` jsou platné pro propojené i vložené položky jsou v (to `COleServerDoc` umožňuje mít společnou implementaci) a funkce, které jsou platné pouze pro vložené objekty jsou umístěny ve třídě (z pohledu serveru, je **dokument,** který je vložený).

Většina zátěže je umístěna na implementátorserveru v tom, že server musí být vědomi faktoru zvětšení kontejneru a podle potřeby upravit jeho rozhraní pro úpravy. Ale jak server určuje faktor zvětšení, který kontejner používá

## <a name="mfc-support-for-zooming"></a>Podpora knihovny MFC pro zvětšování

Aktuální faktor zvětšení lze `COleServerDoc::GetZoomFactor`určit voláním . Volání tohoto, když dokument není aktivní na místě, bude vždy mít za následek 100% faktor zvětšení (nebo poměr 1:1). Volání, zatímco na místě aktivní může vrátit něco jiného než 100%.

Příklad správného přiblížení viz ukázka [HIERSVR](../overview/visual-cpp-samples.md)knihovny MFC OLE . Přiblížení hiersvr je komplikováno skutečností, že zobrazuje text a text obecně neměří lineárním způsobem (rady, typografické konvence, šířky návrhu a výšky věci komplikují). Přesto HIERSVR je rozumný odkaz pro implementaci přiblížení správně, a tak je kurz knihovny MFC [klikyháky](../overview/visual-cpp-samples.md) (krok 7).

`COleServerDoc::GetZoomFactor`určuje faktor zvětšení na základě řady různých metrik, které jsou k `COleServerItem` dispozici `COleServerDoc` z kontejneru nebo z implementace vašeho a tříd. Stručně řečeno, aktuální faktor zvětšení je určen následujícím vzorcem:

```
Position Rectangle (PR) / Container Extent (CE)
```

POZICE OBDÉLNÍK je určen kontejneru. Je vrácena na server během aktivace `COleClientItem::OnGetItemPosition` na místě, když je volána `COleServerDoc::OnSetItemRects` a je aktualizován, když kontejner volá server (s voláním `COleClientItem::SetItemRects`).

Rozsah kontejneru je o něco složitější pro výpočet. Pokud kontejner volal `COleServerItem::OnSetExtent` (s voláním `COleClientItem::SetExtent`), pak rozsah kontejneru je tato hodnota převedena na obrazové body na základě počtu pixelů na logický palec. Pokud kontejner není volána SetExtent (což je obvykle případ), pak `COleServerItem::OnGetExtent`KONTEJNER ROZSAH je velikost vrácena z . Takže pokud kontejner není volána SetExtent, rozhraní předpokládá, že pokud to udělal kontejnerby jej volat s 100 % přirozeného rozsahu (hodnota vrácená z). `COleServerItem::GetExtent` Uvedeno jiným způsobem, rozhraní předpokládá, že kontejner zobrazuje 100 % (ne více, ne méně) položky.

Je důležité si uvědomit, že i když `COleServerItem::OnSetExtent` a `COleServerItem::OnGetExtent` mají podobné názvy, nemají manipulovat se stejným atributem položky. `OnSetExtent`je volána, aby server věděl, kolik objektu je viditelné v kontejneru `OnGetExtent` (bez ohledu na faktor zvětšení) a je volána kontejnerem k určení ideální velikost objektu.

Při pohledu na každé z dotčených api, můžete získat jasnější obrázek:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Tato funkce by měla vrátit "přirozenou velikost" v jednotkách HIMETRIC položky. Nejlepší způsob, jak si myslet o "přirozené velikosti", je definovat ji jako velikost, která se může objevit při tisku. Velikost vrácená zde je konstantní pro konkrétní obsah položky (podobně jako metasoubor, který je konstantní pro konkrétní položku). Tato velikost se nezmění při použití přiblížení na položku. Obvykle se nezmění, když kontejner poskytuje položku více `OnSetExtent`nebo méně místa voláním . Příkladem změny může být jednoduchý textový editor bez možnosti "margin", který zalomený text na základě posledního rozsahu odeslaného kontejnerem. Pokud se server změní, měl by pravděpodobně nastavit OLEMISC_RECOMPOSEONRESIZE bit v systémovém registru (další informace o této možnosti naleznete v dokumentaci k sadě OLE SDK).

## <a name="coleserveritemonsetextent"></a>COleServerItem::Délkarozsahu

Tato funkce je volána, když kontejner zobrazuje "více či méně" objektu. Většina kontejnerů nebude volat to vůbec. Výchozí implementace ukládá poslední hodnotu přijatou z kontejneru v `COleServerDoc::GetZoomFactor` "m_sizeExtent", která se používá při výpočtu výše popsané hodnoty CONTAINER EXTENT.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Tato funkce je volána pouze v případě, že je dokument aktivní na místě. Je volána při kontejneru aktualizuje pozici položky nebo oříznutí použité na položku. POZICE OBDÉLNÍK, jak je popsáno výše, poskytuje čitatel pro výpočet faktor zvětšení. Server může požadovat změnu polohy položky voláním `COleServerDoc::RequestPositionChange`. Kontejner může nebo nemusí reagovat na `OnSetItemRects` tuto žádost `COleServerItem::SetItemRects`voláním (s voláním).

## <a name="coleserverdocondraw"></a>COleServerDoc::Ondraw

Je důležité si uvědomit, že metasoubor `COleServerItem::OnDraw` vytvořený přepsáním vytváří přesně stejný metasoubor, bez ohledu na aktuální faktor zvětšení. Kontejner změní velikost metasouboru podle potřeby. To to je důležitý rozdíl `OnDraw` mezi zobrazení a `OnDraw`položky serveru . Zobrazení zpracovává přiblížení, položka pouze vytvoří *metasoubor se zoomovatelem* a ponechá jej na kontejneru, aby bylo možné provést příslušné přiblížení.

Nejlepší způsob, jak zajistit, aby se server choval správně, je použít implementaci, `COleServerDoc::GetZoomFactor` pokud je dokument aktivní.

## <a name="mfc-support-for-in-place-resizing"></a>Podpora knihovny MFC pro změna velikosti místa

Knihovna MFC plně implementuje rozhraní pro změna velikosti na místě, jak je popsáno ve specifikaci OLE 2. Uživatelské rozhraní je `COleResizeBar` podporováno třídou, vlastní zprávou WM_SIZECHILD a `COleIPFrameWnd`zvláštním zpracováním této zprávy v .

Můžete chtít implementovat jiné zpracování této zprávy, než co je k dispozici v rámci. Jak je popsáno výše, rozhraní opustí výsledky na místě změny velikosti až do kontejneru – server reaguje na změnu faktoru zvětšení. Pokud kontejner reaguje nastavením rozsahu kontejneru a pozice OBDÉLNÍKBĚHEM zpracování jeho `COleClientItem::OnChangeItemPosition` (volána `COleServerDoc::RequestPositionChange`jako výsledek volání ) pak změna velikosti na místě bude mít za následek zobrazení "více či méně" položky v okně úprav. Pokud kontejner reaguje pouhým nastavením polohy OBDÉLNÍK `COleClientItem::OnChangeItemPosition`během zpracování , faktor přiblížení se změní a položka se zobrazí "přibližováno nebo oddáleno".

Server může řídit (do určité míry), co se stane během tohoto vyjednávání. Tabulka se například může rozhodnout zobrazit více nebo méně buněk, když uživatel změní velikost okna při úpravách položky na místě. Textový procesor se může rozhodnout změnit "okraje stránky", takže jsou stejné jako okno a znovu zalomit text na nový okraj. Servery implementovat změnou přirozeného rozsahu `COleServerItem::OnGetExtent`(velikost vrácena z) po dokončení změny velikosti. To způsobí, že obdélník pozice a rozsah kontejneru změnit o stejnou částku, výsledkem je stejný faktor zvětšení, ale větší nebo menší oblast zobrazení. Kromě toho bude více či méně dokumentu viditelné v metasouboru generovaném `OnDraw`. V tomto případě se změní samotný dokument, když uživatel změní velikost položky, nikoli pouze oblast zobrazení.

Můžete implementovat vlastní změna velikosti a stále `COleResizeBar` využívat uživatelské rozhraní poskytované `COleIPFrameWnd` přepsáním WM_SIZECHILD zprávy ve vaší třídě. Další informace o specifikách WM_SIZECHILD viz [technická poznámka 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
