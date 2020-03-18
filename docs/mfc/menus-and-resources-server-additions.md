---
title: 'Nabídky a prostředky: Serverové doplňky'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: c1dfd059572c433e8fd7ccaf6e5c48e880f59cad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445182"
---
# <a name="menus-and-resources-server-additions"></a>Nabídky a prostředky: Serverové doplňky

Tento článek vysvětluje změny, které je třeba provést v nabídkách a dalších prostředcích v aplikaci pro vizuální úpravu serveru (komponenty). Serverová aplikace vyžaduje mnoho dalších přidání do struktury nabídky a další prostředky, protože je možné ji spustit v jednom ze tří režimů: samostatné, vložené nebo na místě. Jak je popsáno v článku [nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md) , existuje maximálně čtyři sady nabídek. Všechny čtyři se používají pro aplikaci MDI s celými servery, zatímco pro miniserver se používají jenom tři. Průvodce aplikací vytvoří rozložení nabídky potřebné pro typ serveru, který chcete. Může být nutné provést některé vlastní úpravy.

Pokud nepoužíváte průvodce aplikací, možná se budete chtít podívat na HIERSVR. RC, skript prostředků pro ukázkovou aplikaci knihovny MFC [HIERSVR](../overview/visual-cpp-samples.md), aby bylo možné zjistit, jak jsou tyto změny implementovány.

Témata, která jsou popsaná v tomto článku, zahrnují:

- [Přidání nabídky serveru](#_core_server_menu_additions)

- [Přidání tabulky akcelerátorů](#_core_server_application_accelerator_table_additions)

- [Přidání tabulky řetězců](../mfc/menus-and-resources-container-additions.md)

- [Miniserver přidání](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a>Přidání nabídky serveru

Aplikace serveru (komponenty) musí mít přidané prostředky nabídky pro podporu úprav vizuálů OLE. Nabídky používané při spuštění aplikace v samostatném režimu není nutné měnit, ale před sestavením aplikace je nutné přidat dva nové prostředky nabídky: jednu pro podporu místní aktivace a jednu pro podporu plně otevřeného serveru. Oba prostředky se používají v aplikacích s úplnými a miniserver aplikacemi.

- Pro podporu místní aktivace musíte vytvořit prostředek nabídky, který je velmi podobný jako prostředek nabídky, který se používá při spuštění v samostatném režimu. Rozdíl v této nabídce je, že položky souborů a oken (a všechny ostatní položky nabídky, které se týkají aplikace, a ne data) chybí. Aplikace kontejneru dodá tyto položky nabídky. Další informace o nástroji a příkladech této nabídky, kterou slučujete, najdete v článcích [nabídky a prostředky: sloučení nabídky](../mfc/menus-and-resources-menu-merging.md).

- Pro zajištění plné otevřené aktivace je nutné vytvořit prostředek nabídky skoro stejně jako prostředek nabídky, který se používá při spuštění v samostatném režimu. Jedinou úpravou tohoto prostředku nabídky je, že některé položky jsou předané, aby odrážely skutečnost, že server pracuje na položce vložené do složeného dokumentu.

Kromě změn uvedených v tomto článku musí váš soubor prostředků zahrnovat AFXOLESV. RC, který je požadován pro implementaci knihovna Microsoft Foundation Class. Tento soubor je v podadresáři MFC\Include.

##  <a name="_core_server_application_accelerator_table_additions"></a>Přidání tabulky akcelerátoru serverové aplikace

Do serverových aplikací musí být přidány dva nové prostředky tabulky akcelerátoru. odpovídají přímo dříve popsaným prostředkům v nabídce. První tabulka akcelerátorů se použije, když se serverová aplikace aktivuje. Skládá se ze všech položek v tabulce akcelerátorů zobrazení s výjimkou těch, které jsou vázané na nabídky soubor a okno.

Druhá tabulka je skoro přesná kopie tabulky akcelerátorů zobrazení. Všechny rozdíly mezi paralelními změnami provedenými v nabídce úplné otevření, které jsou uvedeny v části [Přidání nabídky serveru](#_core_server_menu_additions).

Pokud se například tyto změny v tabulce akcelerátorů změní, porovnejte IDR_HIERSVRTYPE_SRVR_IP a IDR_HIERSVRTYPE_SRVR_EMB tabulky akcelerátorů pomocí IDR_MAINFRAME v HIERSVR. Soubor RC zahrnutý v ukázce [HIERSVR](../overview/visual-cpp-samples.md)knihovny MFC OLE. V vložené tabulce chybí akcelerátory souborů a oken a přesné kopie jsou v vložené tabulce.

##  <a name="_core_string_table_additions_for_server_applications"></a>Přidání tabulkového řetězce pro serverové aplikace

V serverové aplikaci je nutné přidat pouze jednu tabulku řetězců – řetězec, který označuje, že inicializace OLE se nezdařila. Příklad: Zde je položka řetězcové tabulky, kterou průvodce aplikací generuje:

|ID|Řetězec|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicializace technologie OLE se nezdařila. Ujistěte se, že jsou knihovny OLE správné verze.|

##  <a name="_core_mini.2d.server_additions"></a>Miniserver přidání

Stejné dodatky platí pro miniservers, které jsou uvedené výše pro úplné servery. Vzhledem k tomu, že miniserver nelze spustit v samostatném režimu, je jeho hlavní nabídka mnohem menší. Hlavní nabídka vytvořená Průvodcem aplikací obsahuje jenom nabídku soubor, která obsahuje jenom položky Exit a About. Vložené a místní nabídky a akcelerátory pro miniservers jsou stejné jako u úplných serverů.

## <a name="see-also"></a>Viz také

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Nabídky a prostředky: Sloučení nabídky](../mfc/menus-and-resources-menu-merging.md)
