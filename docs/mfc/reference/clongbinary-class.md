---
title: Třída CLongBinary
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
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370138"
---
# <a name="clongbinary-class"></a>Třída CLongBinary

Zjednodušuje práci s velmi velkými binárními datovými objekty (často nazývanými objekty BLOB nebo "binární velké objekty") v databázi.

## <a name="syntax"></a>Syntaxe

```
class CLongBinary : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Vytvoří `CLongBinary` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Obsahuje skutečnou velikost v bajtů datového objektu, jehož popisovač je uložen v aplikaci `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Obsahuje popisovač Windows HGLOBAL pro objekt skutečné bitové kopie.|

## <a name="remarks"></a>Poznámky

Například pole záznamu v tabulce SQL může obsahovat bitmapu představující obrázek. Objekt `CLongBinary` ukládá takový objekt a sleduje jeho velikost.

> [!NOTE]
> Obecně je nyní vhodnější použít [CByteArray](../../mfc/reference/cbytearray-class.md) ve spojení s [funkcí DFX_Binary.](record-field-exchange-functions.md#dfx_binary) Stále můžete `CLongBinary`použít , `CByteArray` ale obecně poskytuje více funkcí v rámci Win32, protože již není `CByteArray`omezení velikosti došlo s 16-bit . Tato rada se vztahuje na programování s objekty přístupu k datům (DAO) a také pro připojení k otevřené databázi (ODBC).

Chcete-li `CLongBinary` použít objekt, deklarujte datový člen pole typu `CLongBinary` ve třídě sady záznamů. Tento člen bude vloženým členem třídy sady záznamů a bude vytvořen při vytvoření sady záznamů. Po `CLongBinary` vytvoření objektu načte mechanismus výměny pole záznamu (RFX) datový objekt z pole v aktuálním záznamu ve zdroji dat a uloží jej zpět do záznamu při aktualizaci záznamu. RFX dotazuje zdroj dat na velikost binární ho velkého objektu, `CLongBinary` přiděluje úložiště pro něj (prostřednictvím datového `m_hData` člena objektu) a ukládá `HGLOBAL` popisovač pro data v `m_hData`. RFX také ukládá skutečnou velikost datového objektu v datovém `m_dwDataLength` prvku. Pracujte s daty `m_hData`v objektu pomocí stejných technik, které byste normálně `HGLOBAL` používali k manipulaci s daty uloženými v popisovači systému Windows.

Když zničíte sadu záznamů, `CLongBinary` vložený objekt je také zničen a jeho `HGLOBAL` destruktor zruší popisovač dat.

Další informace o velkých objektech `CLongBinary`a použití aplikace naleznete v článcích [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md) a [Sada záznamů: Práce s velkými datovými položkami (ODBC).](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary

Vytvoří `CLongBinary` objekt.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Uloží skutečnou velikost v bajtů dat uložených `m_hData`v popisovači HGLOBAL v aplikaci .

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Poznámky

Tato velikost může být menší než velikost bloku paměti přidělené pro data. Volání Win32 [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) funkce získat přidělené velikosti.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

Ukládá popisovač Windows HGLOBAL do skutečných binárních dat velkých objektů.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
