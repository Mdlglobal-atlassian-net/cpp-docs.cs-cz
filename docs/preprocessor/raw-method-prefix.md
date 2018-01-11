---
title: "raw_method_prefix – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_method_prefix
dev_langs: C++
helpviewer_keywords: raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f140bf7d65f620552dea9f2d25f4ae472139b98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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