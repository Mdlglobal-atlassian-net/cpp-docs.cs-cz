---
title: CDynamicAccessor::SetBlobHandling | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs: C++
helpviewer_keywords: SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6117d0ebc2e41ee70900d17dd9a4804c232a070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
Nastaví objekt BLOB zpracování hodnotu pro aktuální řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool SetBlobHandling(  
   DBBLOBHANDLINGENUM eBlobHandling   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Určuje, jak bude zpracovávat data objektů BLOB. Může trvat následující hodnoty:  
  
-   **DBBLOBHANDLING_DEFAULT**: zpracování sloupce dat, které jsou větší než `nBlobSize` (jako nastavte podle `SetBlobSizeLimit`) jako objekt BLOB dat a jejich prostřednictvím načtení `ISequentialStream` nebo `IStream` objektu. Tato možnost se pokusí vytvořit vazbu každý sloupec, který obsahuje data větší než `nBlobSize` nebo uvedené jako **DBTYPE_IUNKNOWN** jako data objektů BLOB.  
  
-   **DBBLOBHANDLING_NOSTREAMS**: zpracování sloupce dat, které jsou větší než `nBlobSize` (jako nastavte podle `SetBlobSizeLimit`) jako objekt BLOB dat a jejich načtení prostřednictvím odkazů v paměti přidělené poskytovatele, vlastněných příjemce. Tato možnost je užitečná pro tabulky, které mají více než jeden sloupec objektů BLOB a poskytovatel podporuje pouze jeden `ISequentialStream` objektu za přistupujícího objektu.  
  
-   **DBBLOBHANDLING_SKIP**: přeskočit (vazba není) sloupce kvalifikující jako obsahující objekty BLOB (přistupující nebude vazby nebo načíst hodnotu sloupce, ale bude stále načíst stav sloupce a délka).  
  
## <a name="remarks"></a>Poznámky  
 By měly volat `SetBlobHandling` před voláním **otevřete**.  
  
 Metody konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) nastaví zpracování hodnota do objektu BLOB **DBBLOBHANDLING_DEFAULT**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)