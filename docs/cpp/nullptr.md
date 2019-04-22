---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 57be8d71f1dac4f347ea6567c02a385719bb7306
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781078"
---
# <a name="nullptr"></a>nullptr

Určuje konstantu nulového ukazatele typu `std::nullptr_t`, který lze převést na libovolný nezpracovaný typ ukazatele.  Přestože lze použít klíčové slovo **nullptr** bez záhlaví, pokud váš kód používá typ `std::nullptr_t`, pak je nutné jej definovat včetně záhlaví `<cstddef>`.

> [!NOTE]
>  **Nullptr** – klíčové slovo je také definováno v C++/rozhraní příkazového řádku pro aplikace spravovaného kódu a není zaměnitelné s normou ISO C++ – klíčové slovo. Pokud váš kód může být zkompilován pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru, která se týká spravovaného kódu, pak použijte `__nullptr` v libovolném řádku kódu, kde je třeba zaručit, že kompilátor používá interpretaci nativního jazyka C++. Další informace najdete v tématu [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Poznámky

Nepoužívejte hodnotu NULL nebo je nula (`0`) jako konstanty nulového ukazatele; **nullptr** je méně ohrožen zneužitím a lépe funguje ve většině situací.  Například zadání `func(std::pair<const char *, double>)` a následné volání `func(std::make_pair(NULL, 3.14))` způsobí chybu kompilátoru.  Makro NULL se rozbalí na `0` tak, aby volání `std::make_pair(0, 3.14)` vrátilo `std::pair<int, double>`, který nelze převést na typ parametru `std::pair<const char *, double>` func().  Volání `func(std::make_pair(nullptr, 3.14))` je úspěšně zkompilováno, protože `std::make_pair(nullptr, 3.14)` vrátí `std::pair<std::nullptr_t, double>`, který lze převést na `std::pair<const char *, double>`.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++vyhodnocovací)