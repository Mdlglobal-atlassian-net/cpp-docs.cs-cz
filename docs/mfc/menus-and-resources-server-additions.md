---
title: 'Nabídky a prostředky: Serverové doplňky'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
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
ms.openlocfilehash: 85c7b6059a868e93c6c6a7ebbd7b08dac3233612
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767196"
---
# <a name="menus-and-resources-server-additions"></a>Nabídky a prostředky: Serverové doplňky

Tento článek vysvětluje změny, které je třeba provést, nabídky a jiné prostředky ve vizuální úpravy aplikace (součást). Serverová aplikace požaduje mnoha funkcemi struktura nabídky a jiné prostředky, protože může být spuštěný v jednom ze tří režimů: stát samostatně, embedded, nebo na místě. Jak je popsáno v [nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md) článek, jsou maximálně čtyři sady nabídek. Všechny čtyři se používají pro aplikace MDI úplný server, jsou pro miniserver využít pouze tři. Průvodce aplikace vytvoří rozložení nabídky nezbytné pro typ serveru, který chcete. Určité přizpůsobení, může být nutné.

Pokud je velmi riskantní používat Průvodce aplikací, můžete se podívat na HIERSVR. RC, skript prostředků pro ukázkovou aplikaci knihovny MFC [HIERSVR](../overview/visual-cpp-samples.md), pokud chcete zobrazit, jak se implementují tyto změny.

V tomto článku probíraná témata zahrnují:

- [Přidání serveru do nabídky](#_core_server_menu_additions)

- [Přidání tabulky akcelerátorů](#_core_server_application_accelerator_table_additions)

- [Přidání tabulky řetězců](../mfc/menus-and-resources-container-additions.md)

- [Přidání miniserver](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> Přidání serveru do nabídky

Aplikace serveru (součást) musí mít prostředky nabídky přidaná kvůli podpoře úpravy s náhledem OLE. Nabídky při spuštění aplikace v samostatném režimu není potřeba změnit, ale musíte přidat dva nové nabídce prostředky před sestavením aplikace: jednu pro podporu aktivace na místě a jednu pro podporu serveru plně otevřený. Úplné a miniserver aplikace používají oba prostředky nabídky.

- Kvůli podpoře aktivace na místě, musíte vytvořit prostředek nabídky, který je velmi podobný nabídce prostředků používá při spuštění v samostatném režimu. Rozdíl v této nabídce je, že chybí soubor a okno položky (a všechny ostatní položky nabídky, které se zabývají aplikace a ne na data). Aplikace typu kontejner poskytne tyto položky nabídky. Další informace o a příklad, tento postup slučování nabídek, najdete v článku [nabídky a prostředky: Slučování nabídek](../mfc/menus-and-resources-menu-merging.md).

- Kvůli podpoře aktivace zcela otevřená, je potřeba vytvořit téměř stejný jako prostředek nabídky, který používá prostředek nabídky při spuštění v samostatném režimu. Pouze změny k tomuto prostředku nabídky je, že některé položky se mění tak, aby odrážely skutečnost, že server pracuje na položku vložený ve složeném dokumentu.

Kromě změny uvedené v tomto článku musí obsahovat AFXOLESV souboru prostředků. RC, která je potřebná pro implementaci knihovny Microsoft Foundation Class. Tento soubor je v podadresáři MFC\Include.

##  <a name="_core_server_application_accelerator_table_additions"></a> Přidání tabulky akcelerátoru aplikace serveru

Dvě nové zdroje tabulky akcelerátoru, musí být přidané do serverové aplikace; odpovídají přímo na nové nabídce prostředky popsaných výše. První tabulky akcelerátorů se používá, když je server aplikace aktivována na místě. Zahrnuje všechny položky v tabulce akcelerátorů zobrazení s výjimkou těch vázané na soubor a okno nabídky.

Druhá tabulka je téměř přesnou kopii tabulky akcelerátorů zobrazení. Případné rozdíly paralelní změny provedené v plně otevřít nabídku podle [přidání do nabídky Server](#_core_server_menu_additions).

Příklad tyto změny tabulky akcelerátoru porovnejte IDR_HIERSVRTYPE_SRVR_IP a IDR_HIERSVRTYPE_SRVR_EMB tabulek akcelerátorů IDR_MAINFRAME v HIERSVR. Soubor RC, které jsou zahrnuté v ukázce MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Přesné kopie jsou vložené tabulky a akcelerátory souboru a okno chybí v tabulce místní.

##  <a name="_core_string_table_additions_for_server_applications"></a> Přidání tabulky řetězců pro serverové aplikace

Přidání tabulky pouze jeden řetězec je nezbytné v serverové aplikaci – řetězec označuje, že inicializace technologie OLE se nezdařila. Například tady je tabulka řetězců položka, která generuje Průvodce aplikací:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Nepovedlo se inicializovat OLE. Ujistěte se, že jsou knihovny OLE správné verze.|

##  <a name="_core_mini.2d.server_additions"></a> Přidání miniserver

Stejné dodatky požádat o miniservers jako ty uvedené výše pro úplné servery. Protože miniserver nelze spustit v samostatném režimu, je mnohem menší jeho hlavní nabídky. V hlavní nabídce vytvořené průvodcem aplikací má pouze nabídku souborů, obsahuje pouze položky, ukončení a o. Vložené a místní nabídky a akcelerátory pro miniservers jsou stejné jako u celé servery.

## <a name="see-also"></a>Viz také:

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Nabídky a prostředky: Slučováním nabídek](../mfc/menus-and-resources-menu-merging.md)
