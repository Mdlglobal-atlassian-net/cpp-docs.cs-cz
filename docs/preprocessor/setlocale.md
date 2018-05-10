---
title: setlocale – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cfabfa3c83fe2ff90a6f7dbe07d5205f7a6f9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="setlocale"></a>setlocale
Určuje národní prostředí (země/oblast a jazyk) při překladu konstant širokého znaku a řetězcových literálů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že se algoritmus převodu vícebajtových znaků na široké znaky může lišit na základě národního prostředí nebo mohou kompilace probíhat v jiném národní prostředí lišícího se od prostředí, kde bude spuštěn spustitelný soubor, poskytuje tato direktiva pragma způsob určení cílového národního prostředí v době kompilace. Tím je zaručeno, že řetězce širokého znaku budou uloženy ve správném formátu.  
  
 Výchozí hodnota *řetězec národního prostředí* je "".  
  
 Národní prostředí „C“ mapuje každý znak v řetězci na jeho hodnotu jako `wchar_t` (unsigned short). Jiné hodnoty, které jsou platné pro `setlocale` jsou ty položky, které jsou součástí [řetězce jazyků](../c-runtime-library/language-strings.md) seznamu. Je například možné setkat se s:  
  
```  
#pragma setlocale("dutch")  
```  
  
 Schopnost vydávat řetězec jazyka závisí na znakové stránce a podpoře ID jazyka na počítači.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)