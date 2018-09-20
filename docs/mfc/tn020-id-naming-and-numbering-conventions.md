---
title: 'TN020: ID konvence pojmenování a číslování | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.id
dev_langs:
- C++
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f19d79b7946e3f2b4fda0b2651ce8d2099373d93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433579"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: Konvence pojmenování a číslování pro identifikátory

Tato poznámka popisuje ID pojmenování a číslování vytváření názvů pro prostředky, příkazy, řetězce, ovládací prvky a podřízená okna používá MFC 2.0.

ID knihovny MFC pojmenování a číslování pro identifikátory konvence jsou určeny pro splnění následujících požadavků:

- Poskytují konzistentní standardní pojmenování ID použít v rámci knihovny MFC a aplikací MFC, které jsou podporovány editor prostředků Visual C++. To usnadňuje programátor k interpretaci typu a původu zdroje z jejího ID.

- Zvýraznit silný vztah 1: 1 mezi určité typy identifikátorů.

- Odpovídat již běžně používaných normy pro pojmenování identifikátorů ve Windows.

- Rozdělení prostoru ID číslování. Čísla ID může přiřadit programátora, MFC, Windows a prostředky upravené jinak Visual C++. Aby nedošlo k duplikaci čísla ID vám pomůže odpovídající dělení.

## <a name="the-id-prefix-naming-convention"></a>Konvence pojmenování předpona ID

Několik typů identifikátorů může dojít v aplikaci. Konvence pojmenovávání ID knihovny MFC definuje různé předpony pro různé typy zdrojů.

Knihovna MFC používá předpona "IDR_" označuje ID prostředku, který se vztahuje na více typů prostředků. Například pro okno daného rámce, knihovna MFC používá stejnou předponu "IDR_" k označení prostředek nabídky, akcelerátoru, řetězec a ikonu. V následující tabulce jsou uvedeny různé předpony a jejich využití:

|Předpona|Použití|
|------------|---------|
|IDR_|Pro více typů prostředků (primárně pro nabídky, akcelerátory a pásů karet).|
|IDD_|Dialogové okno šablony prostředků (například IDD_DIALOG1).|
|IDC_|Pro kurzor prostředky.|
|IDI_|Ikona prostředků.|
|IDB_|Pro prostředky rastrového obrázku.|
|IDS_|Pro řetězcové prostředky.|

V rámci zdroj dialogového okna knihovny MFC dodržovat tyto konvence:

|Předpona nebo popisek|Použití|
|---------------------|---------|
|IDOK IDCANCEL|Pro standardní tlačítko ID.|
|IDC_|Pro ostatní ovládací prvky dialogového okna.|

Pro ukazatele je také použita předpona "IDC_". Tento konflikt názvů není obvykle problém vzhledem k tomu, že Typická aplikace bude mít několik kurzory a mnoho ovládacích prvků dialogového okna.

V nabídce prostředků MFC dodržovat tato konvence:

|Předpona|Použití|
|------------|---------|
|IDM_|Pro položky nabídky, které nepoužívají architekturu příkaz knihovny MFC.|
|ID_|Pro příkazy nabídek, které používají architekturu příkaz knihovny MFC.|

Příkazy, které následují příkaz architektury MFC musí mít obslužné rutiny příkazu ON_COMMAND a může mít obslužnou rutinu ON_UPDATE_COMMAND_UI. Pokud tyto obslužné rutiny příkazů použijte příkaz architektury MFC, budou fungovat správně, jestli jsou vázány na příkaz nabídky, tlačítka panelu nástrojů nebo tlačítko panel dialogového okna. Stejnou předponou "ID_" se používá také pro nabídky výzvy řetězec, který se zobrazí na panelu zpráv dané aplikace. Většina položek nabídky v aplikaci by měly dodržovat konvence příkaz knihovny MFC. Všechny identifikátory standardních příkazů (například id_file_new –) podle Tato konvence.

Knihovna MFC také používá "IDP_" jako specializovaná forma řetězce (namísto "IDS_"). Řetězce s předponou "IDP_" výzvy, tedy řetězců použitých ve okna se zprávou. "IDP_" řetězce mohou obsahovat "%1" a "%2" jako zástupné symboly řetězců určené program. Řetězce "IDP_" obvykle mají témata nápovědy k nim má přiřazené a řetězce "IDS_" tomu tak není. Jsou vždy lokalizované řetězce "IDP_" a "IDS_" řetězce nemusí být lokalizována.

Knihovna MFC také používá předpona "IDW_" jako specializovaná forma ovládací prvek ID (místo "IDC_"). Tyto identifikátory jsou přiřazeny k podřízených oken, jako je například zobrazení a příčky v rámci tříd. ID implementace MFC mají předponu "AFX_".

## <a name="the-id-numbering-convention"></a>Konvence číslování ID

Následující tabulka uvádí platné rozsahy pro ID konkrétní typy. Některá omezení jsou technické implementace omezení a jiné konvence, které jsou navrženy pro vaše ID zabránit kolize s identifikátory předdefinovaných Windows nebo MFC výchozí implementace.

Důrazně doporučujeme, že definujete všechna ID uvnitř doporučené rozsahy. Dolní mez tyto rozsahy je 1, protože se nepoužívá 0. Doporučujeme použít běžné vytváření a použití 100 nebo 101 jako první ID.

|Předpona|Typ prostředku|Platný rozsah|
|------------|-------------------|-----------------|
|IDR_|vícenásobné|1 až 0x6FFF|
|IDD_|šablony dialogu|1 až 0x6FFF|
|IDB_ IDC_ IDI_,|kurzory, ikony, bitmapy|1 až 0x6FFF|
|IDS_ IDP_|Obecné řetězce|1 až 0x7FFF|
|ID_|příkazy|0x8000 až 0xDFFF|
|IDC_|ovládací prvky|8 až 0xDFFF|

Důvodů, proč tato omezení rozsahu:

- Podle konvence se nepoužívá hodnotu ID 0.

- Windows implementace omezení omezit ID menší než nebo rovna hodnotě 0x7FFF true prostředků.

- Interní rámec MFC rezervuje tyto rozsahy:

   - 0x7000 prostřednictvím 0x7FFF (viz afxres.h)

   - 0xE000 prostřednictvím 0xEFFF (viz afxres.h)

   - 16000 prostřednictvím 18000 (viz afxribbonres.h)

     Tyto rozsahy mohou v budoucnu měnit implementace MFC.

- Několika příkazů systému Windows použít rozsah 0xF000 prostřednictvím 0xFFFF.

- ID ovládacího prvku 1 až 7 jsou vyhrazené pro standardní ovládací prvky, jako je například IDOK a IDCANCEL.

- Rozsah 0x8000 prostřednictvím 0xFFFF pro řetězce je vyhrazený pro nabídky vyzve k zadání příkazy.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

