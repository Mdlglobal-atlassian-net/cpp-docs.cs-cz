---
title: "no_registry – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_registry
dev_langs: C++
helpviewer_keywords: no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 347cdd89a8d8c3014a02708c91df3292275f4e3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="noregistry"></a>no_registry
Atribut `no_registry` říká kompilátoru, aby v registru nevyhledával knihovny typů importované pomocí direktivy `#import`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#import filename no_registry  
```  
  
#### <a name="parameters"></a>Parametry  
 *Název souboru*  
 Knihovna typů.  
  
## <a name="remarks"></a>Poznámky  
 Pokud knihovnu odkazovaného typu nebyl nalezen v adresáři zahrnout, kompilace se nezdaří, i když knihovny typů v registru.  `no_registry`šíří do dalších typ knihoven importovat implicitně s `auto_search`.  
  
 Kompilátor nikdy nebude hledat v registru typy knihoven, které jsou určeny názvem souboru a které jsou předány přímo do direktivy `#import`.  
  
 Je-li zadán atribut `auto_search`, další direktivy `#import` budou generovány s nastavením atributu `no_registry` počáteční direktivy `#import` (byla-li počáteční direktiva `#import` vytvořena s atributem `no_registry`, bude direktiva `auto_search` generovaná pomocí atributu `#import` vytvořena také s atributem `no_registry`).  
  
 `no_registry`je užitečné, pokud chcete importovat křížové odkazovaného typu knihovny bez riziko kompilátoru hledání starší verzi souboru v registru.  `no_registry`je také užitečné, pokud není zaregistrován knihovny typů.  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)