---
title: CBookmark::CBookmark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7663c34fc9eea5f4262fea6b347c1b7899ace85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095232"
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