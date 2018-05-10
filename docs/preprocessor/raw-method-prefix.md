---
title: raw_method_prefix – | Microsoft Docs
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
ms.openlocfilehash: 236c9042393e4ff3de57bea83ad566c8b74d5d3b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Konkrétní C++**  
  
 Určuje předponu různých předejdete kolize názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `Prefix`  
 Předpona, kterou chcete použít.  
  
## <a name="remarks"></a>Poznámky  
 Nízké úrovně vlastnosti a metody jsou vystaveny členské funkce s názvem výchozí předponu **raw_** předejdete kolize názvů s vysoké úrovně členské funkce zpracování chyb.  
  
> [!NOTE]
>  Účinky `raw_method_prefix` atribut se nezmění přítomnost [raw_interfaces_only –](#_predir_raw_interfaces_only) atribut. `raw_method_prefix` Vždy má přednost před `raw_interfaces_only` v zadání předpony. Pokud oba atributy se používají ve stejné `#import` příkaz a potom předponu určeného `raw_method_prefix` je použit atribut.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)