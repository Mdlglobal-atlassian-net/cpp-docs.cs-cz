---
title: "setlocale – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs: C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf0cd4d6d77f4479d5a1cfd56f74f83c3980f38f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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