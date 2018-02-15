---
title: CBookmark::CBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd3529272031e779afdc5315d90613867dcbb823
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
Konstruktor  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CBookmark();   

CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nSize`  
 [v] Velikost vyrovnávací paměti záložky v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 První funkce nastaví vyrovnávací paměť na **NULL** a velikost vyrovnávací paměti na hodnotu 0. Funkce second nastaví velikost vyrovnávací paměti na `nSize`a vyrovnávací paměť na bajtové pole `nSize` bajtů.  
  
> [!NOTE]
>  Tato funkce je k dispozici v pouze **CBookmark\<0 >**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CBookmark – třída](../../data/oledb/cbookmark-class.md)