---
title: "Cdaodatabaseinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 085d0e525cb00c9fffb3698080194da92a6dbb8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo – struktura
`CDaoDatabaseInfo` Struktura obsahuje informace o objektu databáze definované pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoDatabaseInfo  
{  
    CString m_strName;       // Primary  
    BOOL m_bUpdatable;       // Primary  
    BOOL m_bTransactions;    // Primary  
    CString m_strVersion;    // Secondary  
    long m_lCollatingOrder;  // Secondary  
    short m_nQueryTimeout;   // Secondary  
    CString m_strConnect;    // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Jedinečné názvy objekt databáze. Chcete-li tuto vlastnost načíst přímo, volejte [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_bUpdatable`  
 Určuje, zda můžete provedeny změny v databázi. Chcete-li tuto vlastnost načíst přímo, volejte [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Podrobnosti naleznete v tématu "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
 *m_bTransactions*  
 Určuje, zda zdroj dat podporuje transakce – záznamu řadu změny, které později možné vrátit zpět (zrušena) nebo potvrdit (Uložit). Pokud je databáze založená na databázový stroj Microsoft Jet, vlastnost transakce je nenulové hodnoty a transakce můžete používat. Další databázové stroje nemusí podporovat transakce. Chcete-li tuto vlastnost načíst přímo, volejte [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Podrobnosti naleznete v tématu "Transakce vlastnost" v nápovědě rozhraní DAO.  
  
 *m_strVersion*  
 Označuje verzi databázového stroje Microsoft Jet. K načtení hodnoty této vlastnosti přímo, volání objekt databáze [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) – členská funkce. Podrobnosti naleznete v tématu "Verze vlastnost" v nápovědě rozhraní DAO.  
  
 `m_lCollatingOrder`  
 Určuje pořadí řazení v textu pro porovnání řetězců nebo řazení. Možné hodnoty patří:  
  
- **dbSortGeneral** použijte obecné pořadí řazení (angličtina, francouzština, němčina, portugalština, italština a moderní španělština).  
  
- **dbSortArabic** použít Arabic řazení.  
  
- **dbSortCyrillic** použít ruština řazení.  
  
- **dbSortCzech** použít České řazení.  
  
- **dbSortDutch** použít Holandská řazení.  
  
- **dbSortGreek** použít řecké řazení.  
  
- **dbSortHebrew** použít hebrejského řazení.  
  
- **dbSortHungarian** použít Maďarská řazení.  
  
- **dbSortIcelandic** použít islandském řazení.  
  
- **dbSortNorwdan** použít Norská nebo Dánská řazení.  
  
- **dbSortPDXIntl** použít Paradox mezinárodní pořadí řazení.  
  
- **dbSortPDXNor** použít Paradox Norská nebo Dánská řazení.  
  
- **dbSortPDXSwe** použít Paradox Švédská nebo Finská řazení.  
  
- **dbSortPolish** použít polština řazení.  
  
- **dbSortSpanish** použít Španělské řazení.  
  
- **dbSortSwedFin** použít Švédská nebo Finská řazení.  
  
- **dbSortTurkish** použít turečtinu řazení.  
  
- **dbSortUndefined** pořadí řazení je neznámé nebo nedefinované.  
  
 Další informace naleznete v tématu "Přizpůsobení Windows registru nastavení pro Data Access" v nápovědě rozhraní DAO.  
  
 *m_nQueryTimeout*  
 Počet sekund, databázového stroje Microsoft Jet čeká, než vypršení časového limitu nastane při spuštění dotazu v databázi ODBC. Výchozí hodnota časového limitu je 60 sekund. Když QueryTimeout nastavena na hodnotu 0, dojde k bez časového limitu; To může způsobit program přestal reagovat. K načtení hodnoty této vlastnosti přímo, volání objekt databáze [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) – členská funkce. Podrobnosti naleznete v tématu "QueryTimeout vlastnost" v nápovědě rozhraní DAO.  
  
 `m_strConnect`  
 Poskytuje informace o zdroji otevřenou databázi. Informace o připojení řetězce a informace o načtení hodnota této vlastnosti přímo najdete v tématu [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) – členská funkce. Další informace naleznete v tématu "Připojit vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="remarks"></a>Poznámky  
 Databáze je objekt DAO základní třída objektu MFC [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) – členská funkce.  
  
 Načte informace [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) – členská funkce je uložen v `CDaoDatabaseInfo` struktura. Volání `GetDatabaseInfo` pro `CDaoWorkspace` objekt v kolekci jejichž databáze je uložený objekt databáze. `CDaoDatabaseInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoDatabaseInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
