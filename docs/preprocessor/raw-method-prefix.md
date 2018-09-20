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
ms.openlocfilehash: fc2a37f587d3b5ac2b695171f5620db6521693d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439676"
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
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)