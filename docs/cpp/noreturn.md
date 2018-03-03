---
title: noreturn | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15df38143ded836b671fdfa17a7c5790a9fe960a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="noreturn"></a>noreturn
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Tento atribut `__declspec` říká kompilátoru, že funkce neprovede navrácení. V důsledku toho kompilátor zná, který kód po volání **__declspec(noreturn)** funkce nedostupný.  
  
 Pokud kompilátor najde funkci s cestou řízení, která nevrací hodnotu, vygeneruje upozornění (C4715) nebo chybovou zprávu (C2202). Pokud cesta ovládacích prvků není dosažitelný kvůli funkci, která nikdy vrátí, můžete použít **__declspec(noreturn)** aby tohoto varování nebo chyby.  
  
> [!NOTE]
>  Přidání **__declspec(noreturn)** funkce, která zpět může mít za následek nedefinované chování.  
  
## <a name="example"></a>Příklad  
 V následující ukázce **else** klauzule neobsahuje příkaz return.  Deklarování `fatal` jako **__declspec(noreturn)** zabraňuje chybě nebo upozornění.  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)