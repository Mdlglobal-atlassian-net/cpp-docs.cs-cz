---
title: raw_method_prefix – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fb9178bc315385bab97cea473430745ad66d973
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465297"
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Specifické pro C++**  
  
Určuje jinou předponu vyhnete kolize názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_method_prefix("Prefix")  
```  
  
### <a name="parameters"></a>Parametry  
*Předpona*  
Předpona, která má být použit.  
  
## <a name="remarks"></a>Poznámky  
 
Nízké úrovně vlastnosti a metody vystaveny členským funkcím pojmenovaným s předponou výchozí **raw_** k vyhnete kolize názvů s vysoké úrovně členské funkce zpracování chyb.  
  
> [!NOTE]
> Účinky **raw_method_prefix –** atribut se nezmění přítomností [raw_interfaces_only](#_predir_raw_interfaces_only) atribut. **Raw_method_prefix –** vždy má přednost před `raw_interfaces_only` v určeném předponu. Pokud oba atributy jsou používány ve stejném `#import` příkaz a pak podle Zadaná předpona **raw_method_prefix –** atribut se používá.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)