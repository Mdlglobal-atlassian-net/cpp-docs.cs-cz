---
title: nullptr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06586d7d4374ec1763e43a1eaf3235c37dc72cd1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077942"
---
# <a name="nullptr"></a>nullptr

Určuje konstantu nulového ukazatele typu `std::nullptr_t`, který lze převést na libovolný nezpracovaný typ ukazatele.  Přestože lze použít klíčové slovo **nullptr** bez záhlaví, pokud váš kód používá typ `std::nullptr_t`, pak je nutné jej definovat včetně záhlaví `<cstddef>`.

> [!NOTE]
>  **Nullptr** – klíčové slovo je také definováno v jazyce C + +/ CLI pro aplikace spravovaného kódu a není zaměnitelné s klíčovým slovem standardu ISO C++. Pokud váš kód může být zkompilován pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru, která se týká spravovaného kódu, pak použijte `__nullptr` v libovolném řádku kódu, kde je třeba zaručit, že kompilátor používá interpretaci nativního jazyka C++. Další informace najdete v tématu [nullptr](../windows/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Poznámky

Nepoužívejte hodnotu NULL nebo je nula (`0`) jako konstanty nulového ukazatele; **nullptr** je méně ohrožen zneužitím a lépe funguje ve většině situací.  Například zadání `func(std::pair<const char *, double>)` a následné volání `func(std::make_pair(NULL, 3.14))` způsobí chybu kompilátoru.  Makro NULL se rozbalí na `0` tak, aby volání `std::make_pair(0, 3.14)` vrátilo `std::pair<int, double>`, který nelze převést na typ parametru `std::pair<const char *, double>` func().  Volání `func(std::make_pair(nullptr, 3.14))` je úspěšně zkompilováno, protože `std::make_pair(nullptr, 3.14)` vrátí `std::pair<std::nullptr_t, double>`, který lze převést na `std::pair<const char *, double>`.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)