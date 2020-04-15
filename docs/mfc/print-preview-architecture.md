---
title: Architektura náhledu tisku
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375948"
---
# <a name="print-preview-architecture"></a>Architektura náhledu tisku

Tento článek vysvětluje, jak rozhraní Knihovny MFC implementuje funkce náhledu tisku. Probíraná témata zahrnují:

- [Proces náhledu tisku](#_core_the_print_preview_process)

- [Úprava náhledu tisku](#_core_modifying_print_preview)

Náhled tisku se poněkud liší od zobrazení obrazovky a tisku, protože namísto přímého kreslení obrazu na zařízení musí aplikace simulovat tiskárnu pomocí obrazovky. Aby tomu bylo možné vyhovět, definuje knihovna tříd Microsoft Foundation speciální (nezdokumentovaná) třídu odvozenou z [třídy CDC](../mfc/reference/cdc-class.md), nazvanou `CPreviewDC`. Všechny `CDC` objekty obsahují dva kontexty zařízení, ale obvykle jsou identické. V `CPreviewDC` objektu se liší: první představuje simulovanou tiskárnu a druhá představuje obrazovku, na které je výstup skutečně zobrazen.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Proces náhledu tisku

Když uživatel vybere příkaz Náhled z nabídky **Soubor,** rozhraní `CPreviewDC` vytvoří objekt. Vždy, když vaše aplikace provede operaci, která nastaví charakteristiku kontextu zařízení tiskárny, rozhraní také provede podobnou operaci v kontextu zařízení obrazovky. Pokud například aplikace vybere písmo pro tisk, rozhraní framework vybere písmo pro zobrazení na obrazovce, které simuluje písmo tiskárny. Vždy, když aplikace odešle výstup do tiskárny, rozhraní místo toho odešle výstup na obrazovku.

Náhled tisku se také liší od tisku v pořadí, v jakém každý kreslí stránky dokumentu. Během tisku bude rozhraní pokračovat v tiskové smyčce, dokud nebude vykreslen určitý rozsah stránek. Během náhledu tisku se kdykoli zobrazí jedna nebo dvě stránky a aplikace čeká; nezobrazí se žádné další stránky, dokud uživatel neodpoví. Během náhledu tisku musí aplikace také reagovat na WM_PAINT zprávy, stejně jako při běžném zobrazení obrazovky.

[CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkce je volána při vyvolání režimu náhledu, stejně jako je na začátku tiskové úlohy. Struktura [struktury CPrintInfo](../mfc/reference/cprintinfo-structure.md) předaná funkci obsahuje několik členů, jejichž hodnoty můžete nastavit pro úpravu určitých charakteristik operace náhledu tisku. Můžete například nastavit *m_nNumPreviewPages* člen, aby určil, zda chcete zobrazit náhled dokumentu v jednostránkovém nebo dvoustránkovém režimu.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Úprava náhledu tisku

Chování a vzhled náhledu tisku můžete poměrně snadno upravit několika způsoby. Můžete například:

- Způsobí, že okno náhledu tisku zobrazí posuvník pro snadný přístup k libovolné stránce dokumentu.

- Způsobit, aby náhled tisku zachoval pozici uživatele v dokumentu tím, že začnete jeho zobrazení na aktuální stránce.

- Způsobte provedení jiné inicializace pro náhled a tisk tisku.

- Způsobí, že náhled tisku zobrazí čísla stránek ve vlastních formátech.

Pokud víte, jak dlouhý je `SetMaxPage` dokument a voláte s příslušnou hodnotou, může rozhraní použít tyto informace v režimu náhledu i během tisku. Jakmile rozhraní dokumentu zná délku dokumentu, může poskytnout oknu náhledu posuvník, který uživateli umožňuje stránkovat dokument v režimu náhledu. Pokud jste nenastavili délku dokumentu, rozhraní framework nemůže umístit posuvník označující aktuální pozici, takže rozhraní nepřidá posuvník. V takovém případě musí uživatel procházet dokumentem pomocí tlačítek Další stránka a Předchozí stránka na ovládacím panelu okna náhledu.

Pro náhled tisku může být užitečné přiřadit hodnotu *m_nCurPage* členovi `CPrintInfo`aplikace , i když byste to nikdy neudělali pro běžný tisk. Během běžného tisku tento člen nese informace z frameworku do třídy zobrazení. To je, jak rozhraní framework sděluje zobrazení, které stránky by měly být vytištěny.

Naproti tomu při spuštění režimu náhledu tisku *m_nCurPage* člen nese informace v opačném směru: z pohledu do rámce. Rozhraní framework používá hodnotu tohoto člena k určení, která stránka by měla být zobrazena jako první. Výchozí hodnota tohoto člena je 1, takže první stránka dokumentu se zobrazí zpočátku. Přepsáním `OnPreparePrinting` můžete nastavit tento člen na číslo stránky, která se zobrazuje v době vyvolání příkazu Náhled. Tímto způsobem aplikace udržuje aktuální pozici uživatele při přechodu z normálního režimu zobrazení do režimu náhledu tisku.

Někdy můžete `OnPreparePrinting` chtít provést jinou inicializaci v závislosti na tom, zda se nazývá tisková úloha nebo náhled. Můžete to určit kontrolou *proměnné m_bPreview* člena `CPrintInfo` ve struktuře. Tento člen je nastaven na **hodnotu TRUE** při vyvolání náhledu tisku.

Struktura `CPrintInfo` také obsahuje člen s názvem *m_strPageDesc*, který se používá k formátování řetězců zobrazených v dolní části obrazovky v jednostránkovém a vícestránkovém režimu. Ve výchozím nastavení jsou tyto řetězce ve tvaru "Stránka *n*" a "Stránky *n* - *m*", ale můžete upravit *m_strPageDesc* zevnitř `OnPreparePrinting` a nastavit řetězce na něco složitějšího. Další informace naleznete v [tématu CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) in the *MFC Reference.*

## <a name="see-also"></a>Viz také

[Tisk a náhled tisku](../mfc/printing-and-print-preview.md)<br/>
[Tisk](../mfc/printing.md)<br/>
[Třída CView](../mfc/reference/cview-class.md)<br/>
[Třída CDC](../mfc/reference/cdc-class.md)
