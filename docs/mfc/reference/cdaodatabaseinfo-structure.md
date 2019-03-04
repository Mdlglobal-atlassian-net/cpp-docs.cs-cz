---
title: CDaoDatabaseInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 920301af6f660aeac010ecbf844b80ea628bbfd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285630"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo – struktura

`CDaoDatabaseInfo` Struktura obsahuje informace o databázový objekt definovaný pro datový přístup k objektům (DAO).

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
Jedinečné názvy databázový objekt. Chcete-li tuto vlastnost načíst přímo, zavolejte [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_bUpdatable*<br/>
Určuje, zda můžete provést změny k databázi. Chcete-li tuto vlastnost načíst přímo, zavolejte [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Podrobnosti naleznete v tématu "Aktualizovat vlastnost" v nápovědě k DAO.

*m_bTransactions*<br/>
Určuje, zda zdroj dat podporuje transakce – záznam řady změn, které lze později vrátit (zrušit) nebo potvrzené (Uložit). Pokud je databáze založená na databázovém stroji Microsoft Jet, vlastnost transakce je nenulový a transakce můžete používat. Ostatní databázové stroje nemusí podporovat transakce. Chcete-li tuto vlastnost načíst přímo, zavolejte [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Podrobnosti naleznete v tématu "Transakce vlastnost" v nápovědě k DAO.

*m_strVersion*<br/>
Určuje verzi modulu databázový stroj Microsoft Jet. K načtení hodnoty této vlastnosti přímo, volání objektu databáze [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) členskou funkci. Podrobnosti naleznete v tématu "Verze vlastnost" v nápovědě k DAO.

*m_lCollatingOrder*<br/>
Určuje pořadí řazení v textu pro porovnání řetězců nebo řazením. Možné hodnoty:

- `dbSortGeneral` Použijte obecné pořadí řazení (angličtina, francouzština, němčina, portugalština, italština a moderní španělština).

- `dbSortArabic` Použijte Arabské řazení.

- `dbSortCyrillic` Pomocí pořadí řazení s ruské.

- `dbSortCzech` Použijte České řazení.

- `dbSortDutch` Použijte Nizozemská řazení.

- `dbSortGreek` Pomocí pořadí řazení řecké abecedy.

- `dbSortHebrew` Použijte hebrejského řazení.

- `dbSortHungarian` Použijte maďarské řazení.

- `dbSortIcelandic` Použijte islandském řazení.

- `dbSortNorwdan` Pořadí řazení Norská nebo Dánská použijte.

- `dbSortPDXIntl` Pomocí pořadí řazení Paradox International.

- `dbSortPDXNor` Použijte Paradox Norská nebo Dánská řazení.

- `dbSortPDXSwe` Použijte Paradox Švédská nebo finština řazení.

- `dbSortPolish` Použijte polská řazení.

- `dbSortSpanish` Pomocí pořadí řazení španělština.

- `dbSortSwedFin` Pořadí řazení Švédská nebo finština použijte.

- `dbSortTurkish` Pomocí pořadí řazení pro turečtinu.

- `dbSortUndefined` Pořadí řazení, je undefined nebo neznámý.

Další informace naleznete v tématu "Přizpůsobení Windows registru nastavení pro přístup k datům" v nápovědě k DAO.

*m_nQueryTimeout*<br/>
Počet sekund, po které databázový stroj Microsoft Jet počká, než vypršení časového limitu vyvolá se při spuštění dotazu na databázi rozhraní ODBC. Výchozí hodnota časového limitu je 60 sekund. Když QueryTimeout je nastavena na hodnotu 0, dojde k žádný časový limit; To může způsobit, že program přestane reagovat. K načtení hodnoty této vlastnosti přímo, volání objektu databáze [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) členskou funkci. Podrobnosti naleznete v tématu "QueryTimeout vlastnost" v nápovědě k DAO.

*m_strConnect*<br/>
Poskytuje informace o zdroji otevřenou databázi. Informace o připojení řetězce a informace o načtení hodnoty této vlastnosti přímo, najdete v článku [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) členskou funkci. Další informace naleznete v tématu "Připojit vlastnost" v nápovědě k DAO.

## <a name="remarks"></a>Poznámky

Databáze je základní objekt třídy knihovny MFC rozhraní DAO objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) členskou funkci.

Načte informace [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) členská funkce je uložen v `CDaoDatabaseInfo` struktury. Volání `GetDatabaseInfo` pro `CDaoWorkspace` objekt v kolekci jehož databáze je uložený objekt databáze. `CDaoDatabaseInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoDatabaseInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
