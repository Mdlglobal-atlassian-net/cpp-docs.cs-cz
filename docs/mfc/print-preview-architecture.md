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
ms.openlocfilehash: 2a57b3c8ef6df46c2e2524cb44dd29d68751389b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569669"
---
# <a name="print-preview-architecture"></a>Architektura náhledu tisku

Tento článek vysvětluje, jak rozhraní MFC framework implementuje funkce náhledu. Probíraná témata zahrnují:

- [Proces náhledu tisku](#_core_the_print_preview_process)

- [Úpravy náhledu tisku](#_core_modifying_print_preview)

Náhled je poněkud liší od obrazovky a tisk, protože místo přímo kreslení obrázku na zařízení, musí aplikace simulovat tiskárny na obrazovce. K tomuto účelu knihovny Microsoft Foundation Class definuje speciální (nedokumentované) třídy odvozené od [třída CDC](../mfc/reference/cdc-class.md), označované jako `CPreviewDC`. Všechny `CDC` objekty obsahují dva kontexty zařízení, ale obvykle jsou identické. V `CPreviewDC` objektu, jsou odlišné: tiskárny se simulované představuje první a druhý představuje obrazovku, na kterém je ve skutečnosti zobrazí výstup.

##  <a name="_core_the_print_preview_process"></a> Proces náhledu tisku

Když uživatel vybere příkaz Náhled tisku z **souboru** vytvoří rámci nabídky, `CPreviewDC` objektu. Pokaždé, když se vaše aplikace provádí operaci, která nastaví vlastnost kontextu zařízení tiskárny, rozhraní také provádí operaci podobně jako na obrazovce kontextu zařízení. Například pokud vaše aplikace vybere písmo pro tisk, rozhraní vybere písmo pro obrazovku, která simuluje písmo tiskárny. Pokaždé, když se vaše aplikace bude posílat výstup na tiskárnu, rozhraní místo toho odesílá výstup na obrazovce.

Náhled se také liší od tisk v pořadí, že každý nakreslí stránky z dokumentu. Během tisku, pokračuje rozhraní tisku smyčky, dokud poskytla určitý rozsah stránek. Během náhledu tisku jednu nebo dvě stránky se zobrazí v každém okamžiku a počká aplikace; dokud uživatel neodpoví, se nezobrazí žádné další stránky. Během náhledu musí aplikace také reagovat na zprávy WM_PAINT, stejně jako při běžné displejem.

[CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkce se volá, když je vyvolána režimu náhledu, stejně, jako je na začátku tiskové úlohy. [Cprintinfo – struktura](../mfc/reference/cprintinfo-structure.md) struktura předaná funkci obsahuje několik členů, jejichž hodnoty lze nastavit na upravit některé vlastnosti operace náhledu tisku. Například můžete nastavit *m_nNumPreviewPages* člen k určení, zda chcete zobrazit náhled dokumentu v režimu jednu nebo dvě stránky.

##  <a name="_core_modifying_print_preview"></a> Úpravy náhledu tisku

Chování a vzhled náhledu různými způsoby, jak můžete místo toho snadno upravit. Například je to možné, mimo jiné:

- Způsobit, že okno náhledu zobrazí posuvník pro zajištění snadného přístupu pro všechny stránky dokumentu.

- Náhled tisku příčina zachovat pozici uživatele v dokumentu podle od jeho zobrazení na aktuální stránce.

- Způsobit různé inicializace mají být provedeny pro náhled tisku a tisk.

- Náhled tisku příčina zobrazíte čísla stránky ve vlastních formátů.

Pokud víte, jak dlouho trvá dokumentu a volání `SetMaxPage` s odpovídající hodnotou rozhraní tyto informace můžete použít v režimu náhledu, stejně jako při tisku. Jakmile rozhraní zná délku dokumentu, může poskytnout okno náhledu se posuvník, které uživateli umožňují stránce vpřed a zpět v dokumentu v režimu náhledu. Pokud jste nenastavili délku dokumentu, rozhraní framework nelze umístit posuvníku označující aktuální pozici, aby rozhraní nepřidává posuvníku. Uživatel v tomto případě musí používat další stránky a předchozí stránky, tlačítka na panelu ovládacího prvku okno náhledu na stránku v dokumentu.

Pro náhled tisku, možná bude užitečné pro přiřazení hodnoty k *m_nCurPage* člen `CPrintInfo`, i když by nikdy uděláte pro běžné tisk. Tento člen během běžné tisk, přenáší informace z architektury do vaší třídy zobrazení. To je, jak rozhraní informuje zobrazení, na stránce, které by měl vytisknout.

Naopak při režim náhledu tisku spuštění, *m_nCurPage* člen přenáší informace v opačném směru: od zobrazení rozhraní framework. Rozhraní používá k určení, na stránce, které by měl být zobrazen nejprve hodnotu tohoto člena. Výchozí hodnota tohoto člena je 1, takže se zpočátku zobrazí první stránka dokumentu. Můžete přepsat `OnPreparePrinting` nastavit na číslo stránky zobrazení v době byla vyvolána příkaz Náhled tohoto člena. Díky tomu aplikace udržuje aktuální pozici uživatele při přesunu z režimu normálního zobrazení na režim náhledu.

Někdy můžete chtít `OnPreparePrinting` k provádění různých inicializace v závislosti na tom, jestli je volána pro tiskové úlohy nebo náhledu tisku. Této služby můžete zjistit kontrolou *m_bPreview* členské proměnné v `CPrintInfo` struktury. Tento člen je nastavený na **TRUE** při vyvolala náhled tisku.

`CPrintInfo` Struktura také obsahuje člen s názvem *m_strPageDesc*, který se používá k formátování řetězce zobrazí v dolní části obrazovky v režimech jednostránkové a více stránek. Ve výchozím nastavení jsou tyto řetězce ve tvaru "stránka *n*" a "stránky *n* - *m*,", ale můžete upravit *m_strPageDesc* z v rámci `OnPreparePrinting` a nastavený řetězce na číslo komplikovanějších. Zobrazit [cprintinfo – struktura](../mfc/reference/cprintinfo-structure.md) v *odkaz knihovny MFC* Další informace.

## <a name="see-also"></a>Viz také

[Tisk a náhled tisku](../mfc/printing-and-print-preview.md)<br/>
[Tisk](../mfc/printing.md)<br/>
[CView – třída](../mfc/reference/cview-class.md)<br/>
[CDC – třída](../mfc/reference/cdc-class.md)
