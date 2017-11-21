---
title: nullptr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: nullptr_cpp
dev_langs: C++
helpviewer_keywords: nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9d032653b004e0960922efee59924ab120793fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nullptr"></a>nullptr
Určuje konstantu nulového ukazatele typu `std::nullptr_t`, který lze převést na libovolný nezpracovaný typ ukazatele.  I když je možné použít klíčové slovo `nullptr` bez záhlaví, používá-li kód typ `std::nullptr_t`, je nutné jej definovat včetně záhlaví `<cstddef>`.  
  
> [!NOTE]
>  Klíčové slovo `nullptr` je také definováno v C++/CLI pro aplikace se spravovaným kódem a není zaměnitelné s klíčovým slovem Standardu ISO C++. Pokud váš kód může být zkompilovány pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru, která cílí spravovaného kódu, potom použijte `__nullptr` v každý řádek kódu, kde musí zaručit, že kompilátor používá nativní C++ interpretace. Další informace najdete v tématu [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Poznámky  
 Vyhněte se použití `NULL` nebo nuly (`0`) jako konstanty nulového ukazatele; `nullptr` je méně ohrožen zneužitím a lépe funguje ve většině situací.  Například zadání `func(std::pair<const char *, double>)` a následné volání `func(std::make_pair(NULL, 3.14))` způsobí chybu kompilátoru.  Makro NULL se rozbalí na `0` tak, aby volání `std::make_pair(0, 3.14)` vrátilo `std::pair<int, double>`, který nelze převést na typ parametru `std::pair<const char *, double>` func().  Volání `func(std::make_pair(nullptr, 3.14))` je úspěšně zkompilováno, protože `std::make_pair(nullptr, 3.14)` vrátí `std::pair<std::nullptr_t, double>`, který lze převést na `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)