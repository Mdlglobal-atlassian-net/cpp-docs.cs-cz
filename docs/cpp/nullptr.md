---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358845"
---
# <a name="nullptr"></a>nullptr

Určuje konstantu nulového ukazatele typu `std::nullptr_t`, který lze převést na libovolný nezpracovaný typ ukazatele.  I když můžete použít klíčové slovo **nullptr** bez zahrnutí `std::nullptr_t`záhlaví, pokud váš kód používá `<cstddef>`typ , pak je nutné definovat zahrnutím záhlaví .

> [!NOTE]
> Klíčové slovo **nullptr** je také definováno v jazyce C++/CLI pro aplikace spravovaného kódu a není zaměnitelné s klíčovým slovem ISO Standard C++. Pokud váš kód může být kompilován pomocí [/clr](../build/reference/clr-common-language-runtime-compilation.md) kompilátor `__nullptr` možnost, která se zaměřuje na spravovaný kód, použijte v libovolném řádku kódu, kde je nutné zaručit, že kompilátor používá nativní interpretace Jazyka C++. Další informace naleznete v [tématu nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Poznámky

Nepoužívejte hodnotu`0`NULL nebo nulu ( ) jako konstantu ukazatele null; **nullptr** je méně náchylné ke zneužití a funguje lépe ve většině situací.  Například zadání `func(std::pair<const char *, double>)` a následné volání `func(std::make_pair(NULL, 3.14))` způsobí chybu kompilátoru.  Makro NULL se rozbalí na `0` tak, aby volání `std::make_pair(0, 3.14)` vrátilo `std::pair<int, double>`, který nelze převést na typ parametru `std::pair<const char *, double>` func().  Volání `func(std::make_pair(nullptr, 3.14))` je úspěšně zkompilováno, protože `std::make_pair(nullptr, 3.14)` vrátí `std::pair<std::nullptr_t, double>`, který lze převést na `std::pair<const char *, double>`.

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
