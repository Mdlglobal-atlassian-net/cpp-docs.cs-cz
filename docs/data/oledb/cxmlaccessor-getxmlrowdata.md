---
title: CXMLAccessor::GetXMLRowData | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 147a79a4d9db17ac0f418356ba45909d02d93c06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103148"
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
Získá celý obsah tabulky řádek jako řetězec ve formátu XML data.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,   
   bool bAppend = false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `strOutput`  
 [out] Odkaz na vyrovnávací paměť obsahující data tabulky, které mají být načteny. Data je naformátován jako data řetězce s názvy – značka XML, které odpovídají úložiště dat názvy sloupců.  
  
 *bAppend*  
 [v] Logická hodnota určující, zda chcete přidat řetězec na konec výstupní data.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek znázorňuje způsob formátování data řádku v kódu XML. `DATA` níže představuje data řádku. Použití přesunout metody pro přechod na požadovaný řádek.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)