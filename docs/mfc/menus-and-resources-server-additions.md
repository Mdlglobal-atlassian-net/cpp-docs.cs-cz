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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375978"
---
# <a name="menus-and-resources-server-additions"></a>Nabídky a prostředky: Serverové doplňky

Tento článek vysvětluje změny, které je třeba provést v nabídkách a dalších prostředcích v aplikaci pro vizuální úpravy serveru (součást). Serverová aplikace vyžaduje mnoho dodatků ke struktuře nabídky a další prostředky, protože lze spustit v jednom ze tří režimů: samostatně, vložené nebo na místě. Jak je popsáno v článku [Nabídky a prostředky (OLE),](../mfc/menus-and-resources-ole.md) existují maximálně čtyři sady nabídek. Všechny čtyři se používají pro aplikaci MDI full-server, zatímco pouze tři se používají pro miniserver. Průvodce aplikací vytvoří rozložení nabídky nezbytné pro požadovaný typ serveru. Některé přizpůsobení může být nezbytné.

Pokud nepoužijete průvodce aplikací, můžete se podívat na HIERSVR. RC, skript prostředků pro ukázkovou aplikaci knihovny MFC [HIERSVR](../overview/visual-cpp-samples.md), zobrazíte způsob implementace těchto změn.

Témata uvedená v tomto článku zahrnují:

- [Přidání nabídky serveru](#_core_server_menu_additions)

- [Doplňky tabulek akcelerátoru](#_core_server_application_accelerator_table_additions)

- [Přidání tabulky řetězců](../mfc/menus-and-resources-container-additions.md)

- [Doplňky miniserverů](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Přidání nabídky serveru

Serverové (komponentové) aplikace musí mít přidány prostředky nabídky pro podporu vizuálních úprav OLE. Nabídky používané při spuštění aplikace v samostatném režimu není nutné měnit, ale před sestavením aplikace je nutné přidat dva nové prostředky nabídky: jeden pro podporu aktivace na místě a jeden pro podporu plně otevřeného serveru. Oba zdroje nabídky jsou využívány full- a miniserveraplikacemi.

- Chcete-li podporovat aktivaci na místě, musíte vytvořit prostředek nabídky, který je velmi podobný prostředku nabídky používanému při spuštění v samostatném režimu. Rozdíl v této nabídce je, že chybí položky souboru a okna (a všechny ostatní položky nabídky, které se zabývají aplikací, a nikoli data). Kontejner aplikace bude dodávat tyto položky nabídky. Další informace o této technice slučování nabídek a jeho příklad naleznete v článku [Nabídky a zdroje: Sloučení nabídky](../mfc/menus-and-resources-menu-merging.md).

- Chcete-li podporovat plně otevřenou aktivaci, musíte vytvořit prostředek nabídky téměř totožný s prostředkem nabídky používaným při spuštění v samostatném režimu. Jedinou úpravou tohoto prostředku nabídky je, že některé položky jsou přeformulovány tak, aby odrážely skutečnost, že server pracuje s položkou vloženou do složeného dokumentu.

Kromě změn uvedených v tomto článku musí soubor prostředků zahrnout AFXOLESV. RC, který je vyžadován pro implementaci knihovny tříd Microsoft Foundation. Tento soubor je v podadresáři Knihovna MFC\Zahrnout.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Přidání tabulek akcelerátoru aplikací serveru

Do serverových aplikací musí být přidány dva nové prostředky tabulky akcelerátoru. odpovídají přímo novým dříve popsaným zdrojům nabídky. První tabulka akcelerátoru se používá při aktivaci serverové aplikace na místě. Skládá se ze všech položek v tabulce akcelerátoru zobrazení s výjimkou těch, které jsou vázány na nabídky Soubor a Okno.

Druhá tabulka je téměř přesnou kopií tabulky akcelerátorů zobrazení. Jakékoli rozdíly paralelní změny provedené v plně otevřené nabídce uvedené v [menu Server Dodatky](#_core_server_menu_additions).

Příklad těchto změn v tabulce akcelerátoru porovnejte tabulky IDR_HIERSVRTYPE_SRVR_IP a IDR_HIERSVRTYPE_SRVR_EMB akcelerátoru s IDR_MAINFRAME v HIERSVR. RC soubor obsažený ve vzorku KNIHOVNY OLE [HIERSVR](../overview/visual-cpp-samples.md). V tabulce na místě chybí akcelerátory souborů a oken a jejich přesné kopie jsou v vložené tabulce.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Přidání tabulky řetězců pro serverové aplikace

Pouze jeden řetězec tabulka sčítání je nutné v aplikaci serveru – řetězec znamenat, že inicializace OLE se nezdařilo. Zde je zde položka tabulky řetězců, kterou generuje průvodce aplikací:

|ID|Řetězec|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicializace OLE se nezdařila. Ujistěte se, že knihovny OLE jsou správná verze.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Doplňky miniserverů

Stejné dodatky platí pro miniservery jako ty, které jsou uvedeny výše pro full-servery. Vzhledem k tomu, že miniserver nelze spustit v samostatném režimu, jeho hlavní nabídka je mnohem menší. Hlavní nabídka vytvořená průvodcem aplikací obsahuje pouze nabídku Soubor, která obsahuje pouze položky Exit a About. Integrované a místní nabídky a akcelerátory pro miniservery jsou stejné jako u full-servers.

## <a name="see-also"></a>Viz také

[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Nabídky a prostředky: Sloučení nabídky](../mfc/menus-and-resources-menu-merging.md)
