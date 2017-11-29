---
title: nothrow (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: nothrow_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82370900fc96c97665cb35351605db86c9ff4faf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nothrow-c"></a>nothrow (C++)
**Konkrétní Microsoft**  
  
 Rozšířený atribut `__declspec`, který lze použít v deklaracích funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento atribut oznamuje kompilátoru, že deklarovaná funkce a funkce, které volá, nikdy nevyvolají výjimku. V modelu synchronního zpracování výjimek, který je nyní výchozí, může kompilátor odstranit mechanismus sledování životnosti určitých nerozvinutelných objektů v takové funkci a významně tak snížit velikost kódu. S využitím následující direktivy preprocesoru jsou tři deklarace funkce uvedené níže ekvivalentní:  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 Použití deklarace `void __declspec(nothrow) __stdcall f2();` má výhodu, že prostřednictvím definic rozhraní API, například těch, které jsou uvedeny v příkazu `#define`, lze snadno zadat klíčové slovo `nothrow` pro sadu funkcí. Třetí deklarace`, void __stdcall f3() throw();` je syntaxí definovanou standardem C++.  
  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)