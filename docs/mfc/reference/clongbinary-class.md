---
title: CLongBinary – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: b75016c6c783ae19d8e0f6739adaa34b8da977db
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338434"
---
# <a name="clongbinary-class"></a>CLongBinary – třída
Zjednodušuje práci s velmi velkými binárními datovými objekty (často nazývané objekty BLOB nebo "binární rozsáhlé objekty") v databázi.  
  
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
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Obsahuje skutečnou velikost v bajtech datového objektu, jehož popisovač je uložen v `m_hData`.|  
|[CLongBinary::m_hData](#m_hdata)|Obsahuje Windows HGLOBAL popisovač pro objekt skutečný obraz.|  
  
## <a name="remarks"></a>Poznámky  
 Pole záznamu v tabulce SQL může například obsahovat rastrový obrázek představující obrázek. A `CLongBinary` objekt ukládá takového objektu a uchovává informace o jeho velikost.  
  
> [!NOTE]
>  Obecně je doporučeno teď použít [CByteArray](../../mfc/reference/cbytearray-class.md) ve spojení s [dfx_binary –](record-field-exchange-functions.md#dfx_binary) funkce. Můžete dál používat `CLongBinary`, ale obecně `CByteArray` přinese další funkce v systému Win32, protože není už omezení velikosti s 16 bitů `CByteArray`. Toto doporučení platí pro programování pomocí objektů DAO (Data Access) a také připojení ODBC (Open Database).  
  
 Použití `CLongBinary` objektu, deklarujte datový člen pole typu `CLongBinary` ve své třídě sady záznamů. Tento člen bude vloženého člena třídy sady záznamů a bude vytvořen při sady záznamů je vytvořený. Po `CLongBinary` objekt je vytvořen, mechanismus pole záznamu (RFX) systému exchange načte objekt data z pole v aktuální záznam ve zdroji dat a uloží je zpět do záznamu při aktualizaci záznamu. RFX dotazuje zdroje dat pro velikost binárního velkého objektu alokují prostor pro něj (prostřednictvím `CLongBinary` objektu `m_hData` datový člen) a ukládá `HGLOBAL` zpracování dat v `m_hData`. RFX také ukládá skutečnou velikost datového objektu v `m_dwDataLength` datový člen. Práce s daty v objektu prostřednictvím `m_hData`, pomocí stejné techniky, které běžně používáte pro manipulaci s daty uloženými v Windows `HGLOBAL` zpracovat.  
  
 Při zrušení sady záznamů, vložený `CLongBinary` také zničení objektu a jeho destruktor uvolní `HGLOBAL` popisovač data.  
  
 Další informace o velké objekty a použití `CLongBinary`, najdete v článcích [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md) a [sada záznamů: práce se velké datové položky (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb_.h  
  
##  <a name="clongbinary"></a>  CLongBinary::CLongBinary  
 Vytvoří `CLongBinary` objektu.  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength  
 Ukládá skutečnou velikost v bajtech dat uložených v úchytu HGLOBAL `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato velikost může být menší než velikost bloku paměti přidělené pro data. Volání Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593) funkce získáte přidělená velikost.  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 Uloží popisovač Windows HGLOBAL data skutečné binárního rozsáhlého objektu.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
