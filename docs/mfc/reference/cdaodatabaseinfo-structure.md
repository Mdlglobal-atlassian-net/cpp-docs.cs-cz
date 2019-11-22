---
title: CDaoDatabaseInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 60972aa3ecaef4d38c9a0d0ecc70477796aa37aa
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304252"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo – struktura

Struktura `CDaoDatabaseInfo` obsahuje informace o databázovém objektu definovaném pro objekty DAO (Data Access Objects). Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

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

*m_strName*<br/>
Jedinečný název databázového objektu. Chcete-li získat přímo tuto vlastnost, zavolejte [CDaoDatabase:: GetName](../../mfc/reference/cdaodatabase-class.md#getname). Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost názvu".

*m_bUpdatable*<br/>
Určuje, zda lze v databázi provést změny. Chcete-li načíst tuto vlastnost přímo, zavolejte [CDaoDatabase:: CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "Aktualizovatelná vlastnost".

*m_bTransactions*<br/>
Označuje, zda zdroj dat podporuje transakce – záznam řady změn, které mohou být později vráceny zpět (zrušeny) nebo potvrzeny (uloženo). Pokud je databáze založená na databázovém stroji Microsoft Jet, je vlastnost Transactions nenulová a můžete použít transakce. Jiné databázové moduly nemusí podporovat transakce. Chcete-li načíst tuto vlastnost přímo, zavolejte [CDaoDatabase:: CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Podrobnosti najdete v tématu "vlastnost transakcí" v nápovědě k rozhraní DAO.

*m_strVersion*<br/>
Označuje verzi databázového stroje Microsoft Jet. Chcete-li načíst hodnotu této vlastnosti přímo, zavolejte členskou funkci [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) objektu databáze. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost verze".

*m_lCollatingOrder*<br/>
Určuje pořadí řazení v textu pro porovnání a řazení řetězců. Možné hodnoty:

- `dbSortGeneral` použít řazení Obecné (v angličtině, francouzštině, němčině, portugalštině, italštině a moderní španělštině).

- `dbSortArabic` použít arabské řazení.

- `dbSortCyrillic` použít pořadí řazení v ruštině.

- `dbSortCzech` použít český způsob řazení.

- `dbSortDutch` použít nizozemské pořadí řazení.

- `dbSortGreek` použít řecké pořadí řazení.

- `dbSortHebrew` použít Hebrejské pořadí řazení.

- `dbSortHungarian` použít maďarské pořadí řazení.

- `dbSortIcelandic` použít pořadí řazení v islandském.

- `dbSortNorwdan` použít norské nebo dánské pořadí řazení.

- `dbSortPDXIntl` použít mezinárodní pořadí řazení pro Paradox.

- `dbSortPDXNor` použít řazení norského nebo dánského pořadí řazení.

- `dbSortPDXSwe` použít pořadí řazení švédské nebo finské.

- `dbSortPolish` použít polský způsob řazení.

- `dbSortSpanish` použít španělskou objednávku řazení.

- `dbSortSwedFin` použít pořadí řazení švédského nebo finského.

- `dbSortTurkish` použít turecké pořadí řazení.

- `dbSortUndefined` pořadí řazení není definováno nebo není známo.

Další informace najdete v tématu Přizpůsobení nastavení registru Windows pro přístup k datům v nápovědě k rozhraním DAO.

*m_nQueryTimeout*<br/>
Doba v sekundách, po kterou bude databázový stroj Microsoft Jet čekat, než dojde k vypršení časového limitu, když se dotaz spustí v databázi ODBC. Výchozí hodnota časového limitu je 60 sekund. Když je QueryTimeout nastavené na 0, neproběhne žádný časový limit; To může způsobit, že program přestane reagovat. Chcete-li načíst hodnotu této vlastnosti přímo, zavolejte členskou funkci [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) objektu databáze. Podrobnosti najdete v tématu "vlastnost QueryTimeout" v nápovědě k rozhraní DAO.

*m_strConnect*<br/>
Poskytuje informace o zdroji otevřené databáze. Informace o tom, jak propojit řetězce, a informace o tom, jak přímo načíst hodnotu této vlastnosti, naleznete v tématu členská funkce [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Další informace najdete v nápovědě k rozhraní DAO v tématu "připojení vlastnosti".

## <a name="remarks"></a>Poznámky

Databáze je objekt DAO, jehož základem je objekt knihovny MFC třídy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odkazy na primární, sekundární a všechny výše označují, jak jsou informace vráceny členskou funkcí [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

Informace načtené členskou funkcí [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) jsou uloženy ve struktuře `CDaoDatabaseInfo`. Vyvolejte `GetDatabaseInfo` pro objekt `CDaoWorkspace`, ve kterém databáze je uložena kolekce databázových objektů. `CDaoDatabaseInfo` také definuje členskou funkci `Dump` v sestaveních ladění. K výpisu obsahu `CDaoDatabaseInfo` objektu můžete použít `Dump`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
