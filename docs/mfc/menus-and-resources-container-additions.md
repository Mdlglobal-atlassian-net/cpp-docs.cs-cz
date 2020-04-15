---
title: 'Nabídky a prostředky: Kontejnerové doplňky'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364795"
---
# <a name="menus-and-resources-container-additions"></a>Nabídky a prostředky: Kontejnerové doplňky

Tento článek vysvětluje změny, které je třeba provést v nabídkách a dalších prostředcích v aplikaci kontejneru vizuální úpravy.

V kontejnerových aplikacích je třeba provést dva typy změn: změny existujících prostředků pro podporu vizuálních úprav OLE a přidání nových prostředků používaných pro aktivaci na místě. Pokud k vytvoření aplikace kontejneru použijete průvodce aplikací, budou tyto kroky provedeny za vás, ale mohou vyžadovat určité přizpůsobení.

Pokud nepoužijete průvodce aplikací, můžete se podívat na OCLIENT. RC, skript prostředků pro ukázkovou aplikaci OCLIENT, chcete-li zjistit, jak jsou implementovány tyto změny. Viz ukázka knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

Témata uvedená v tomto článku zahrnují:

- [Přidání nabídky kontejneru](#_core_container_menu_additions)

- [Doplňky tabulek akcelerátoru](#_core_container_application_accelerator_table_additions)

- [Přidání tabulky řetězců](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Přidání nabídky kontejneru

Do nabídky Úpravy musíte přidat následující položky:

|Položka|Účel|
|----------|-------------|
|**Vložit nový objekt**|Otevře dialogové okno Vložit objekt OLE a vloží do dokumentu propojenou nebo vloženou položku.|
|**Vložit odkaz**|Vloží odkaz na položku ve schránce do dokumentu.|
|**Ole sloveso**|Volá primární sloveso vybrané položky. Text této položky nabídky se změní tak, aby odrážel primární sloveso vybrané položky.|
|**Odkazy**|Otevře dialogové okno Ole Upravit vazby a změní existující propojené položky.|

Kromě změn uvedených v tomto článku musí zdrojový soubor obsahovat afxolecl. RC, který je vyžadován pro implementaci knihovny tříd Microsoft Foundation. Vložit nový objekt je jediným povinným přidáním nabídky. Další položky mohou být přidány, ale ty zde uvedené jsou nejběžnější.

Pokud chcete podporovat místní aktivaci obsažených položek, musíte vytvořit novou nabídku pro aplikaci kontejneru. Tato nabídka se skládá ze stejné nabídky Soubor a rozbalovacích nabídek Okna, které se používají při otevření souborů, ale mezi nimi jsou umístěny dva oddělovače. Tyto oddělovače se používají k označení, kde server (součást) položka (aplikace) by měla umístit své nabídky při aktivaci na místě. Další informace o této technice slučování nabídek naleznete v [tématu Nabídky a zdroje: Sloučení nabídek](../mfc/menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Přidání tabulek akcelerátoru aplikací kontejneru

Malé změny prostředků tabulky akcelerátoru aplikace kontejneru jsou nezbytné, pokud podporujete aktivaci na místě. První změna umožňuje uživateli stisknout klávesu escape (ESC) pro zrušení režimu úprav na místě. Do hlavní tabulky akcelerátoru přidejte následující položku:

|ID|Klíč|Typ|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

Druhou změnou je vytvoření nové tabulky akcelerátoru, která odpovídá novému prostředku nabídky vytvořenému pro místní aktivaci. Tato tabulka obsahuje položky pro nabídky Soubor a Okno kromě výše uvedené položky VK_ESCAPE. Následující příklad je tabulka akcelerátoru vytvořená pro aktivaci na místě ve [vzorovém kontejneru](../overview/visual-cpp-samples.md)knihovny MFC :

|ID|Klíč|Typ|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Přidání tabulky řetězců pro kontejnerové aplikace

Většina změn v řetězcových tabulkách pro aplikace kontejnerů odpovídá dalším položkám nabídky uvedeným v [dodatku nabídky kontejneru](#_core_container_menu_additions). Zadávají text zobrazený ve stavovém řádku při zobrazení každé položky nabídky. Zde jsou zde položky tabulky řetězců, které generuje průvodce aplikací:

|ID|Řetězec|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicializace OLE se nezdařila. Ujistěte se, že knihovny OLE jsou správná verze.|
|IDP_FAILED_TO_CREATE|Vytvoření objektu se nezdařilo. Ujistěte se, že je objekt zadán do systémového registru.|

## <a name="see-also"></a>Viz také

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md)
