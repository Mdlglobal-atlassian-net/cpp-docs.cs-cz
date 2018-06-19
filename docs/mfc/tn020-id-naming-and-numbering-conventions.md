---
title: 'TN020: ID konvence pojmenování a číslování | Microsoft Docs'
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
ms.openlocfilehash: 17b27b4cfc1b624c9c12138154a660951a0f2a13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384108"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: Konvence pojmenování a číslování pro identifikátory
Tato poznámka popisuje ID pojmenování a číslování konvence, které používá MFC 2.0 pro prostředky, příkazy, řetězce, ovládací prvky a podřízená okna.  
  
 Konvence pojmenování MFC ID a číslování mají splňovat následující požadavky:  
  
-   Poskytují konzistentní standardní pojmenování ID používané v rámci celé knihovny MFC a knihovny MFC aplikace, které jsou podporovány pomocí editoru prostředků Visual C++. Díky tomu je snazší pro programátory interpretovat typu a původu prostředku z jeho ID.  
  
-   Zvýraznit silný vztah 1: 1 mezi určité typy identifikátorů.  
  
-   Odpovídají standardům již často používaný pro pojmenování ID v systému Windows.  
  
-   Místo číslování ID oddílu. Čísla ID jde přiřadit programátory, MFC, Windows a upravit Visual C++ prostředky. Odpovídající dělení předejdete duplikace čísla ID.  
  
## <a name="the-id-prefix-naming-convention"></a>Předpona ID konvence pojmenování  
 Několik typů ID, může dojít v aplikaci. Konvence pojmenování MFC ID definuje různé předpon pro různé typy prostředků.  
  
 MFC použije předpona "IDR_" ID prostředku, který se vztahuje na více typů prostředků. Například pro okno daného rámce, používá MFC stejnou předponu "IDR_" k označení prostředků nabídky, akcelerátoru, řetězec a ikona. Následující tabulka uvádí různé předpony a jejich využití:  
  
|Předpona|Použití|  
|------------|---------|  
|IDR_|Pro více typů prostředků (primárně pro nabídek, akcelerátorů a pásů karet).|  
|IDD_|Pro dialogové okno šablony prostředky (například IDD_DIALOG1).|  
|IDC_|Pro kurzor prostředky.|  
|IDI_|Ikona prostředků.|  
|IDB_|Pro prostředky rastrového obrázku.|  
|IDS_|Pro řetězcové prostředky.|  
  
 V rámci zdroj dialogového okna knihovny MFC dodržovat tyto konvence:  
  
|Předpona nebo popisek|Použití|  
|---------------------|---------|  
|IDOK IDCANCEL|Pro standardní tlačítko ID.|  
|IDC_|Pro další ovládací prvky dialogového okna.|  
  
 Předpona "IDC_" se také používá pro kurzory. Tato ke konfliktu názvů není obvykle problém protože Typická aplikace bude mít několik kurzory a mnoho ovládací prvky dialogového okna.  
  
 V nabídce prostředku MFC dodržovat tyto konvence:  
  
|Předpona|Použití|  
|------------|---------|  
|IDM_|Pro položky nabídky, které nepoužívají architektury MFC příkaz.|  
|ID_|Příkazy nabídky, použijte příkaz architektury MFC.|  
  
 Příkazy, které následují příkaz architektury MFC musí mít `ON_COMMAND` příkaz obslužné rutiny a může mít `ON_UPDATE_COMMAND_UI` obslužné rutiny. Pokud tyto obslužné rutiny příkazů postupovat podle příkaz architektury MFC, budou fungovat správně jestli jsou vázány na příkazu nabídky, tlačítka panelu nástrojů nebo tlačítko panel dialogového okna. Nabídky výzva řetězec, který se zobrazí na panelu zpráv programu se také používá stejnou předponu "ID_". Konvence příkaz MFC by mělo vycházet většinu položek nabídky v aplikaci. Všechny standardní identifikátory příkazů (například `ID_FILE_NEW`) postupujte podle touto konvencí.  
  
 "IDP_" MFC také používá jako specializovaná forma řetězce (místo "IDS_"). Řetězce s předponou "IDP_" jsou výzvy, který je řetězce použité v oknech zprávy. Řetězce "IDP_" může obsahovat "%1" a "%2" zástupnými symboly řetězců určen program. Řetězce "IDP_" obvykle mají témata nápovědy související s nimi a řetězce "IDS_" nepodporují. Jsou vždy lokalizované řetězce "IDP_" a nemusí být lokalizované řetězce "IDS_".  
  
 Knihovny MFC také používá předpona "IDW_" jako specializovaná forma řízení ID (místo "IDC_"). Tyto identifikátory přiřazené k podřízená okna například zobrazení a příčky třídy framework. ID implementace MFC mají předponu "AFX_".  
  
## <a name="the-id-numbering-convention"></a>Konvence ID číslování  
 Následující tabulka uvádí platném rozsahu pro konkrétní typy identifikátorů. Některá omezení jsou technickou implementaci omezení a jiné jsou konvence, které jsou navrženy tak, aby vaše ID vzájemné kolizi předdefinovaná identifikátory Windows nebo MFC výchozí implementace.  
  
 Důrazně doporučujeme definovat všechna ID uvnitř doporučené rozsahy. Dolní limit tyto rozsahy je 1, protože se nepoužívá 0. Doporučujeme používat běžné konvence a použít 100 nebo 101 jako první ID.  
  
|Předpona|Typ prostředku|Platný rozsah|  
|------------|-------------------|-----------------|  
|IDR_|vícenásobné|1 až 0x6FFF|  
|IDD_|šablony dialogu|1 až 0x6FFF|  
|IDB_ IDC_, IDI_,|kurzory, ikony, rastrové obrázky|1 až 0x6FFF|  
|IDS_ IDP_|Obecné řetězce|1 až 0x7FFF|  
|ID_|příkazy|0x8000 prostřednictvím 0xDFFF|  
|IDC_|ovládací prvky|8 až 0xDFFF|  
  
 Důvody pro tyto limity rozsahu:  
  
-   Podle konvence není použita hodnota ID 0.  
  
-   Omezení implementace systému Windows omezit ID být menší než nebo rovno 0x7FFF true prostředků.  
  
-   Knihovny MFC framework interní si vyhrazuje těchto oblastí:  
  
    -   0x7000 prostřednictvím 0x7FFF (viz afxres.h)  
  
    -   0xE000 prostřednictvím 0xEFFF (viz afxres.h)  
  
    -   16000 prostřednictvím 18000 (viz afxribbonres.h)  
  
     Tyto rozsahy mohou v budoucnu měnit MFC implementace.  
  
-   Několik příkazů systému Windows použít rozsah 0xF000 prostřednictvím 0xFFFF.  
  
-   ID ovládacího prvku 1 až 7 jsou vyhrazené pro standardní ovládací prvky, jako je například IDOK a IDCANCEL.  
  
-   Rozsah 0x8000 prostřednictvím 0xFFFF pro řetězce je vyhrazený pro nabídky výzvy pro příkazy.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

