---
title: CXMLAccessor::GetXMLRowData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs: C++
helpviewer_keywords: GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b21e48439fbf4f420751e2f89903044626df9c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
Získá celý obsah tabulky řádek jako řetězec ve formátu XML data.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetXMLRowData(   
   CSimpleStringW& strOutput,   
   bool bAppend = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `strOutput`  
 [out] Odkaz na vyrovnávací paměť obsahující data tabulky, které mají být načteny. Data je naformátován jako data řetězce s názvy – značka XML, které odpovídají úložiště dat názvy sloupců.  
  
 *bAppend*  
 [v] Logická hodnota určující, zda chcete přidat řetězec na konec výstupní data.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek znázorňuje způsob formátování data řádku v kódu XML. `DATA`níže představuje data řádku. Použití přesunout metody pro přechod na požadovaný řádek.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)