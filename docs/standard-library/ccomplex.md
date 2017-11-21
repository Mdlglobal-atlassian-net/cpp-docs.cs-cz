---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <ccomplex>
dev_langs: C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 677c2ec66bdf8f7b210f96a30aaf7722b43fb035
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
Obsahuje hlavičku standardní knihovna C++ [ \<komplexní >](../standard-library/complex.md), což zahrnuje efektivně hlavičku knihovny standardní C \<complex.h > a přidá přidružené jména `std` obor názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Včetně tuto hlavičku zajistí, že jsou názvy deklarováno s použitím externí propojení v hlavičce knihovny standardní C deklarované v `std` oboru názvů.  
  
 Název `clog`, kterého je deklarovaná v \<complex.h >, není definován v `std` obor názvů kvůli možným konfliktům s `clog` deklarovaného v souboru [ \<iostream >](../standard-library/iostream.md).  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)



