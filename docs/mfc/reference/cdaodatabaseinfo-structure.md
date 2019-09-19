---
title: CDaoDatabaseInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 46d8056ee4ab478b65f3ef0bd59d88bd3af9b28c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096162"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo – struktura

`CDaoDatabaseInfo` Struktura obsahuje informace o databázovém objektu definovaném pro objekty DAO (Data Access Objects).
Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

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

- `dbSortGeneral`Použijte řazení Obecné (v angličtině, francouzštině, němčině, portugalštině, italštině a moderní španělštině).

- `dbSortArabic`Použijte arabské pořadí řazení.

- `dbSortCyrillic`Použijte pořadí řazení v ruštině.

- `dbSortCzech`Použijte pořadí řazení v češtině.

- `dbSortDutch`Použijte nizozemské pořadí řazení.

- `dbSortGreek`Použijte řecké pořadí řazení.

- `dbSortHebrew`Použijte Hebrejské pořadí řazení.

- `dbSortHungarian`Použijte maďarské pořadí řazení.

- `dbSortIcelandic`Použijte pořadí řazení v islandském.

- `dbSortNorwdan`Použijte norské nebo dánské pořadí řazení.

- `dbSortPDXIntl`Použijte mezinárodní pořadí řazení pro Paradox.

- `dbSortPDXNor`Použijte pořadí řazení v programu Paradox Norština nebo Dánština.

- `dbSortPDXSwe`Použijte pořadí řazení švédské nebo finské.

- `dbSortPolish`Použijte úhledné pořadí řazení.

- `dbSortSpanish`Použijte pořadí řazení v španělštině.

- `dbSortSwedFin`Použijte pořadí řazení švédského nebo finského.

- `dbSortTurkish`Použijte turecké pořadí řazení.

- `dbSortUndefined`Pořadí řazení není definováno nebo je neznámé.

Další informace najdete v tématu Přizpůsobení nastavení registru Windows pro přístup k datům v nápovědě k rozhraním DAO.

*m_nQueryTimeout*<br/>
Doba v sekundách, po kterou bude databázový stroj Microsoft Jet čekat, než dojde k vypršení časového limitu, když se dotaz spustí v databázi ODBC. Výchozí hodnota časového limitu je 60 sekund. Když je QueryTimeout nastavené na 0, neproběhne žádný časový limit; To může způsobit, že program přestane reagovat. Chcete-li načíst hodnotu této vlastnosti přímo, zavolejte členskou funkci [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) objektu databáze. Podrobnosti najdete v tématu "vlastnost QueryTimeout" v nápovědě k rozhraní DAO.

*m_strConnect*<br/>
Poskytuje informace o zdroji otevřené databáze. Informace o tom, jak propojit řetězce, a informace o tom, jak přímo načíst hodnotu této vlastnosti, naleznete v tématu členská funkce [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Další informace najdete v nápovědě k rozhraní DAO v tématu "připojení vlastnosti".

## <a name="remarks"></a>Poznámky

Databáze je objekt DAO, jehož základem je objekt knihovny MFC třídy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odkazy na primární, sekundární a všechny výše označují, jak jsou informace vráceny členskou funkcí [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

Informace načtené členskou funkcí [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) jsou uloženy ve `CDaoDatabaseInfo` struktuře. Volání `GetDatabaseInfo`objektu,ve kterémdatabázejeuloženakolekcedatabázovýchobjektů.`CDaoWorkspace` `CDaoDatabaseInfo`také definuje `Dump` členskou funkci v sestavení ladění. Můžete použít `Dump` k výpisu obsahu `CDaoDatabaseInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
