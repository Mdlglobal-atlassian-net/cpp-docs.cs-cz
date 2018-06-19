---
title: CLongBinary – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7030fdcb59166c0e70a7b2c2471273c913fe459
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368017"
---
# <a name="clongbinary-class"></a>CLongBinary – třída
Zjednodušuje pracovat s objekty velké binární data (často říká objektů BLOB, nebo "binární rozsáhlé objekty") v databázi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|Vytvoří `CLongBinary` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Obsahuje skutečná velikost v bajtech datový objekt, jehož popisovač je uložen v `m_hData`.|  
|[CLongBinary::m_hData](#m_hdata)|Obsahuje Windows `HGLOBAL` popisovač objektu skutečný obrázek.|  
  
## <a name="remarks"></a>Poznámky  
 Pole záznamu v tabulce SQL může například obsahovat rastrový obrázek představující obrázku. A `CLongBinary` objekt ukládá takového objektu a uchovává informace o jeho velikost.  
  
> [!NOTE]
>  Obecně platí, je lepší postupem teď použít [CByteArray](../../mfc/reference/cbytearray-class.md) ve spojení s [dfx_binary –](record-field-exchange-functions.md#dfx_binary) funkce. Můžete dál používat `CLongBinary`, ale obecně `CByteArray` poskytuje další funkce v prostředí Win32, vzhledem k tomu, že je už omezení velikosti s 16bitové `CByteArray`. Toto doporučení se k programování s objekty DAO (Data Access), jakož i připojení ODBC (Open Database).  
  
 Použít `CLongBinary` objekt, deklarovat pole datových členů typu `CLongBinary` ve vaší třídy sady záznamů. Tento člen bude embedded členem třídy sady záznamů a bude vypočten-li sada záznamů je vytvořená. Po `CLongBinary` vytvoření objektu, mechanismus pole záznamu (exchange – RFX) načte datový objekt z pole v aktuálním záznamu ve zdroji dat a uloží je zpět do záznamu při aktualizaci záznamu. RFX dotazuje zdroj dat pro velikost binární rozsáhlý objekt přiděluje úložiště pro něj (pomocí `CLongBinary` objektu `m_hData` – datový člen) a ukládá `HGLOBAL` zpracování dat v `m_hData`. RFX také ukládá skutečná velikost datového objektu v `m_dwDataLength` – datový člen. Práce s daty v objektu prostřednictvím `m_hData`, pomocí stejné techniky, které běžně používáte k manipulaci s daty uloženými v systému Windows `HGLOBAL` zpracování.  
  
 Při zrušení sady záznamů, vložený `CLongBinary` objektu je také zrušen a zruší její destruktor přidělení `HGLOBAL` popisovač data.  
  
 Další informace o rozsáhlé objekty a využívat `CLongBinary`, najdete v článcích [záznamů (ODBC)](../../data/odbc/recordset-odbc.md) a [sada záznamů: práce s velké datové položky (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb_.h  
  
##  <a name="clongbinary"></a>  CLongBinary::CLongBinary  
 Vytvoří `CLongBinary` objektu.  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength  
 Ukládá skutečná velikost v bajtech dat uložených v `HGLOBAL` zpracování v `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato velikost může být menší než velikost bloku paměti přidělené pro data. Volání Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593) funkce získat přidělená velikost.  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 Ukládá Windows `HGLOBAL` zpracování dat skutečný binární rozsáhlý objekt.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
