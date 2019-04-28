---
title: 'Nabídky a prostředky: Kontejnerové doplňky'
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
ms.openlocfilehash: b1a74fef743592d3d052226dac926fc7ddc58578
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363463"
---
# <a name="menus-and-resources-container-additions"></a>Nabídky a prostředky: Kontejnerové doplňky

Tento článek vysvětluje změny, které je třeba provést, nabídky a jiné prostředky ve vizuální úpravy aplikace typu kontejner.

V kontejneru aplikace potřeba provést dva druhy změny: změny stávajících prostředků, abyste podporují vizuální úpravy OLE a přidání nové prostředky používané pro aktivace na místě. Pokud používáte Průvodce aplikací k vytvoření aplikace v kontejneru, tyto kroky se provede za vás, ale vyžadují určité přizpůsobení.

Pokud je velmi riskantní používat Průvodce aplikací, můžete se podívat na OCLIENT. RC, skript prostředků pro OCLIENT ukázkovou aplikaci, pokud chcete zobrazit, jak se implementují tyto změny. Najdete v ukázce MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

V tomto článku probíraná témata zahrnují:

- [Přidání do nabídky kontejneru](#_core_container_menu_additions)

- [Přidání tabulky akcelerátorů](#_core_container_application_accelerator_table_additions)

- [Přidání tabulky řetězců](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> Přidání do nabídky kontejneru

Do nabídky Úpravy je nutné přidat následující položky:

|Položka|Účel|
|----------|-------------|
|**Vložit nový objekt**|Otevře dialogové okno vložení objektu OLE pro vložení propojené nebo vložené položky do dokumentu.|
|**Vložit odkaz**|Vloží odkaz na položku do schránky do dokumentu.|
|**OLE Verb**|Volá primárního operaci vybranou položku. Textové změny této nabídky položky tak, aby odrážely primárního operaci vybrané položky.|
|**Odkazy**|Otevře dialogové okno úpravy odkazů OLE, chcete-li změnit existující propojené položky.|

Kromě změny uvedené v tomto článku zdrojový soubor musí obsahovat AFXOLECL. RC, která je potřebná pro implementaci knihovny Microsoft Foundation Class. Vložit nový objekt je pouze požadovaná nabídky. Můžete přidat další položky, ale jsou zde uvedeny jsou nejčastěji používané.

Pokud chcete, aby podporoval aktivaci na místě upravovat položky, je nutné vytvořit novou nabídku pro svou aplikaci typu kontejner. Tato nabídka se skládá z stejnou nabídku Soubor a použít, když jsou otevřené soubory, ale má dva oddělovače umístěná mezi oběma rozbalovací nabídky okna. Tyto oddělovače slouží k označení, kde položka serveru (součást) (aplikace) by měl umístit nabídky při aktivaci na místě. Další informace o této techniky slučování nabídek, naleznete v tématu [nabídky a prostředky: Slučování nabídek](../mfc/menus-and-resources-menu-merging.md).

##  <a name="_core_container_application_accelerator_table_additions"></a> Přidání tabulky akcelerátoru aplikace kontejneru

Malé změny aplikace typu kontejner prostředků tabulky akcelerátorů jsou nezbytné, pokud podporujete aktivace na místě. První změna umožňuje uživateli stisknout klávesu escape (ESC) pro zrušení režim úprav na místě. Přidejte následující položku do tabulky hlavní akcelerátoru:

|ID|Key|Type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

Druhý změnu je vytvoření nové tabulky akcelerátoru, která odpovídá na nový prostředek nabídky, které jsou vytvořené pro aktivace na místě. Tato tabulka obsahuje záznamy pro nabídky soubor a okno kromě výše uvedených vk_escape – zadání. V následujícím příkladu je tabulka akcelerátoru vytvořena pro aktivace na místě v ukázce MFC [KONTEJNERU](../overview/visual-cpp-samples.md):

|ID|Key|Type|
|--------|---------|----------|
|ID_FILE_NEW|CTRL + N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE –|SHIFT+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> Přidání tabulky řetězců pro aplikace typu kontejner

Většina změn do tabulek řetězců pro aplikace typu kontejner odpovídají další položky nabídky podle [přidání do nabídky kontejneru](#_core_container_menu_additions). Text zobrazený ve stavovém řádku v případě každé položky nabídky se zobrazí dodávají. Jako příklad uvádíme položky tabulky řetězců, které generuje Průvodce aplikací:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Nepovedlo se inicializovat OLE. Ujistěte se, že jsou knihovny OLE správné verze.|
|IDP_FAILED_TO_CREATE|Nepovedlo se vytvořit objekt. Ujistěte se, že se objekt zadal do systémového registru.|

## <a name="see-also"></a>Viz také:

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md)
