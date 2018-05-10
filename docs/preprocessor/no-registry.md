---
title: no_registry – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 416663592f4362c110637fb4d4b4b418d9776cde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
 Pokud knihovnu odkazovaného typu nebyl nalezen v adresáři zahrnout, kompilace se nezdaří, i když knihovny typů v registru.  `no_registry` šíří do dalších typ knihoven importovat implicitně s `auto_search`.  
  
 Kompilátor nikdy nebude hledat v registru typy knihoven, které jsou určeny názvem souboru a které jsou předány přímo do direktivy `#import`.  
  
 Je-li zadán atribut `auto_search`, další direktivy `#import` budou generovány s nastavením atributu `no_registry` počáteční direktivy `#import` (byla-li počáteční direktiva `#import` vytvořena s atributem `no_registry`, bude direktiva `auto_search` generovaná pomocí atributu `#import` vytvořena také s atributem `no_registry`).  
  
 `no_registry` je užitečné, pokud chcete importovat křížové odkazovaného typu knihovny bez riziko kompilátoru hledání starší verzi souboru v registru.  `no_registry` je také užitečné, pokud není zaregistrován knihovny typů.  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)