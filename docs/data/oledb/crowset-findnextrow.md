---
title: CRowset::FindNextRow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs:
- C++
helpviewer_keywords:
- FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4afc1db20970102ecddb9031f4f1b7a8f6906cf4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098215"
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
Vyhledá další odpovídající řádek po zadanou záložkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT FindNextRow(DBCOMPAREOP op,   
  BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `op`  
 [v] Operace pro použití v porovnání hodnot řádků. Hodnoty, najdete v části [IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx).  
  
 `pData`  
 [v] Ukazatel na hodnotu lze porovnat.  
  
 `wType`  
 [v] Určuje datový typ část hodnoty vyrovnávací paměti. Informace o typu indikátory najdete v tématu [datové typy](https://msdn.microsoft.com/en-us/library/ms723969.aspx) v *referenční příručka programátora technologie OLE DB* ve Windows SDK.  
  
 `nLength`  
 [v] Délka v bajtech přidělené hodnota dat struktury dat příjemce. Podrobnosti najdete v tématu Popis **cbMaxLen** v [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx) v *referenční příručka programátora technologie OLE DB.*  
  
 `bPrecision`  
 [v] Maximální přesnost používá při získávání data. Použít pouze v případě `wType` je `DBTYPE_NUMERIC`. Další informace najdete v tématu [převody zahrnující DBTYPE_NUMERIC nebo DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 `bScale`  
 [v] Škálování při získávání dat používat. Použít pouze v případě `wType` je `DBTYPE_NUMERIC` nebo **DBTYPE_DECIMAL**. Další informace najdete v tématu [převody zahrnující DBTYPE_NUMERIC nebo DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 *bSkipCurrent*  
 [v] Počet řádků z záložku, od kterého má začít vyhledávání.  
  
 `pBookmark`  
 [v] Záložka pro pozice, kdy má být spuštění vyhledávání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje volitelné rozhraní **IRowsetFind**, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetFind** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
 Informace o použití záložek uživatele najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx)