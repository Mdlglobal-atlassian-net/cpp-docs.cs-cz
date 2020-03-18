---
title: OLE – přetažení
description: Přehled rozhraní Microsoft Foundation Classes (MFC) přetažení OLE, jak implementovat zdroj přetažení, cíl přetažení a jak přizpůsobit přetahování.
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: c601e8f0324510346513dc8da48dd1a83c95bceb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420349"
---
# <a name="ole-drag-and-drop"></a>OLE – přetažení

Funkce přetažení objektu OLE je primárně zkratka pro kopírování a vkládání dat. Když použijete schránku ke zkopírování nebo vložení dat, vyžaduje se několik kroků. Vyberete data a v nabídce **Úpravy** zvolíte **Vyjmout** nebo **Kopírovat** . Pak přejdete do cílové aplikace nebo okna a umístíte kurzor do cílového umístění. Nakonec v nabídce zvolíte příkaz **upravit** > **Vložit** .

Funkce přetažení OLE je odlišná od mechanismu přetažení Správce souborů. Správce souborů může zpracovat pouze názvy souborů a je navržen speciálně pro předávání názvů souborů do aplikací. Přetahování OLE je mnohem obecnější. Umožňuje přetahovat všechna data, která by se mohla umístit do schránky.

Když přetáhnete OLE, odeberete z procesu dva kroky. Vyberete data ze zdrojového okna ("zdroj"), pak ho přetáhnete do cílového umístění ("cíl přetažení"). Přetažením myši uvolníte tlačítko myši. Operace eliminuje nutnost nabídek a je rychlejší než sekvence kopírování/vkládání. Existuje pouze jeden požadavek: musí být otevřen i cíl přetažení a alespoň částečně viditelný na obrazovce.

Pomocí přetažení OLE můžete data snadno přenést z jednoho umístění do druhého: v rámci dokumentu, mezi různými dokumenty nebo mezi aplikacemi. Může být implementována buď v kontejneru, nebo v serverové aplikaci. Libovolná aplikace může být vrženým zdrojem, cílem přetažení nebo obojím. Pokud aplikace implementuje podporu drop-source i Drop-Target, můžete přetahovat mezi podřízenými okny nebo v rámci jednoho okna. Díky této funkci se vaše aplikace mnohem snadněji používá.

Články [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) vysvětlují, jak implementovat přenos dat ve vašich aplikacích. Je také užitečné si prohlédnout ukázky knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="implement-a-drop-source"></a>Implementace zdroje přetažení

Chcete-li, aby vaše aplikace poskytovala data pro operaci přetažení, implementujete zdroj přetažení. Základní implementace zdroje odkládacího umístění je poměrně jednoduchá. Prvním krokem je určit, které události zahájí operaci přetažení. Doporučené pokyny pro uživatelské rozhraní definují začátek operace přetažení, jako když dojde k události **WM_LBUTTONDOWN** v bodě uvnitř některých vybraných dat. Ukázky knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md) dodržujte tyto pokyny.

Pokud je vaše aplikace kontejner a vybraná data jsou propojený nebo vložený objekt typu `COleClientItem`, zavolejte jeho členskou funkci `DoDragDrop`. V opačném případě Sestavte objekt `COleDataSource`, inicializujte ho pomocí výběru a zavolejte členskou funkci `DoDragDrop` objektu zdroje dat. Pokud je vaše aplikace Server, použijte `COleServerItem::DoDragDrop`. Informace o přizpůsobení standardního chování při přetahování najdete v části [přizpůsobení](#customize-drag-and-drop)přetahování.

Pokud `DoDragDrop` vrátí **DROPEFFECT_MOVE**, odstraňte zdrojová data ze zdrojového dokumentu hned. Žádná jiná návratová hodnota z `DoDragDrop` nemá žádný vliv na zdroj přetažení.

Další informace najdete v tématu [datové objekty OLE a zdroje dat: vytváření a ničení](../mfc/data-objects-and-data-sources-creation-and-destruction.md) a [datové objekty OLE a zdroje dat:\. manipulace](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="implement-a-drop-target"></a>Implementace cíle přetažení

Implementace cíle přetažení, než je zdroj vyřazení, bude poněkud větší, ale je stále poměrně jednoduché.

### <a name="to-implement-an-ole-drop-target"></a>Implementace cíle přetažení OLE

1. Pokud tam ještě není, přidejte volání `AfxOleInit` do členské funkce `InitInstance` vaší aplikace. Toto volání je vyžadováno pro inicializaci knihoven OLE.

1. Přidejte členskou proměnnou do každého zobrazení v aplikaci, kterou chcete umístit jako cíl přetažení. Tato členská proměnná musí být typu `COleDropTarget` nebo z něj odvozená třída.

1. Z funkce třídy zobrazení, která zpracovává zprávu **WM_CREATE** (obvykle `OnCreate`) volejte členskou funkci nové členské proměnné `Register`. `Revoke` bude při zničení zobrazení automaticky volána za vás.

1. Přepište následující funkce. Pokud chcete stejné chování v celé aplikaci, popište tyto funkce ve vaší třídě zobrazení. Pokud chcete upravit chování v izolovaných případech nebo chcete povolit vyřazení na jiné než`CView` Windows, přepište tyto funkce ve vaší třídě odvozené `COleDropTarget`.

   | Prioritu | Povolení |
   | -------- | -------- |
   | `OnDragEnter` | V okně dojde k odtažení operací. Volá se, když ukazatel poprvé vstoupí do okna. |
   | `OnDragLeave` | Zvláštní chování v případě, že operace přetažení opustí určené okno. |
   | `OnDragOver` | V okně dojde k odtažení operací. Volá se, když se ukazatel myši přetáhne přes okno. |
   | `OnDrop` | Zpracování dat zahozených do určeného okna. |
   | `OnScrollBy` | Speciální chování při nutnosti posouvání v cílovém okně |

Podívejte se na MAINVIEW. Soubor CPP, který je součástí ukázkového [OCLIENT](../overview/visual-cpp-samples.md) knihovny MFC OLE, pro příklad, jak tyto funkce pracují dohromady.

Další informace najdete v tématu [datové objekty OLE a zdroje dat: vytváření a ničení](../mfc/data-objects-and-data-sources-creation-and-destruction.md) a [datové objekty OLE a zdroje dat:\. manipulace](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="customize-drag-and-drop"></a>Přizpůsobení přetahování

Výchozí implementace funkce přetažení je pro většinu aplikací dostačující. Některé aplikace ale můžou vyžadovat, abyste toto standardní chování změnili. V této části najdete popis kroků potřebných ke změně těchto výchozích hodnot. Tento postup můžete použít k vytvoření aplikací, které nepodporují složené dokumenty do drop sources.

Pokud přidáváte standardní chování OLE při přetahování nebo pokud máte aplikaci, která není typu OLE, je nutné vytvořit objekt `COleDataSource`, který bude obsahovat data. Když uživatel spustí operaci přetažení, váš kód by měl volat funkci `DoDragDrop` z tohoto objektu místo z jiných tříd, které podporují operace přetažení.

Volitelně můžete vytvořit objekt `COleDropSource` pro řízení přetažení a přepsání některých jeho funkcí v závislosti na typu chování, které chcete změnit. Tento objekt drop-source se pak předává `COleDataSource::DoDragDrop` a mění výchozí chování těchto funkcí. Tyto různé možnosti umožňují značnou flexibilitu v tom, jak v aplikaci podporujete operace přetahování myší. Další informace o zdrojích dat najdete v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md).

Můžete přepsat následující funkce a přizpůsobit tak operace přetažení:

| Prioritu | Přizpůsobení |
| -------- | ------------ |
| `OnBeginDrag` | Způsob, jakým se zahájí operace přetažení po volání `DoDragDrop`. |
| `GiveFeedback` | Vizuální zpětná vazba, jako je například vzhled kurzoru, pro různé výsledky vyřazení. |
| `QueryContinueDrag` | Ukončení operace přetažení. Tato funkce umožňuje kontrolovat stavy modifikačních kláves během operace přetažení. |

## <a name="see-also"></a>Viz také

\ [OLE](../mfc/ole-in-mfc.md)
\ [datových objektů OLE a datových zdrojů](../mfc/data-objects-and-data-sources-ole.md)
[Datové objekty OLE a zdroje dat: vytvoření a zničení](../mfc/data-objects-and-data-sources-creation-and-destruction.md)\
[Datové objekty OLE a zdroje dat: manipulace](../mfc/data-objects-and-data-sources-manipulation.md)\
[COleClientItem::D odragdrop](../mfc/reference/coleclientitem-class.md#dodragdrop)\
\ [třídy COleDataSource –](../mfc/reference/coledatasource-class.md)
[COleDataSource –::D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)\
\ [třídy COleDropSource](../mfc/reference/coledropsource-class.md)
\ [třídy COleDropTarget](../mfc/reference/coledroptarget-class.md)
[CView:: OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
