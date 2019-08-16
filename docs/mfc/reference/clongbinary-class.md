---
title: CLongBinary – – třída
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505675"
---
# <a name="clongbinary-class"></a>CLongBinary – – třída

Zjednodušuje práci s velmi rozsáhlými binárními datovými objekty (často nazývanými objekty blob nebo "binárními velkými objekty") v databázi.

## <a name="syntax"></a>Syntaxe

```
class CLongBinary : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|`CLongBinary` Vytvoří objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Obsahuje skutečnou velikost v bajtech datového objektu, jehož popisovač je uložen v `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Obsahuje popisovač Windows HGLOBAL pro skutečný objekt obrázku.|

## <a name="remarks"></a>Poznámky

Například pole záznamu v tabulce SQL může obsahovat rastrový obrázek, který představuje obrázek. `CLongBinary` Objekt ukládá takový objekt a uchovává jeho velikost.

> [!NOTE]
>  Obecně je vhodné používat [CByteArray](../../mfc/reference/cbytearray-class.md) ve spojení s funkcí [DFX_Binary](record-field-exchange-functions.md#dfx_binary) . Stále můžete používat `CLongBinary`, ale obecně `CByteArray` poskytuje více funkcí v systému Win32, protože již neexistují omezení velikosti s 16 bity `CByteArray`. Tato doporučení se vztahují na programování s rozhraním DAO (Data Access Object) a také na rozhraní ODBC (Open Database Connectivity).

Chcete-li `CLongBinary` použít objekt, deklarujte datový člen pole typu `CLongBinary` v třídě sady záznamů. Tento člen bude vloženým členem třídy sady záznamů a bude vytvořen při sestavení sady záznamů. Po vytvoření `CLongBinary` objektu objekt výměny pole záznamu (RFX) načte datový objekt z pole v aktuálním záznamu ve zdroji dat a uloží jej zpět na záznam při aktualizaci záznamu. RFX dotazuje zdroj dat pro velikost binárního rozsáhlého objektu, přidělí úložiště `CLongBinary` pro něj (prostřednictvím `m_hData` datového členu objektu `HGLOBAL` ) a ukládá popisovač do dat v `m_hData`. RFX také ukládá skutečnou velikost datového objektu v `m_dwDataLength` datovém členu. Pracujte s daty v objektu `m_hData`pomocí stejných technik, jako byste normálně použili k manipulaci s daty uloženými v popisovači systému Windows. `HGLOBAL`

Při zničení sady záznamů je také zničen vložený `CLongBinary` objekt a jeho destruktor zruší přidělení `HGLOBAL` popisovače dat.

Další informace o velkých objektech a použití `CLongBinary`naleznete v článcích [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md) a [sada záznamů: Práce s velkými datovými položkami (ODBC](../../data/odbc/recordset-working-with-large-data-items-odbc.md)).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb_. h

##  <a name="clongbinary"></a>CLongBinary –:: CLongBinary –

`CLongBinary` Vytvoří objekt.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

Ukládá skutečnou velikost v bajtech dat uložených v popisovači HGLOBAL v `m_hData`.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Poznámky

Tato velikost může být menší než velikost bloku paměti vyhrazeného pro data. Pro získání přidělené velikosti zavolejte funkci Win32 [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) .

##  <a name="m_hdata"></a>  CLongBinary::m_hData

Ukládá HGLOBAL popisovač Windows do skutečných binárních dat o velkém objektu.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
