---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177765"
---
# <a name="nullptr"></a>nullptr

Určuje konstantu nulového ukazatele typu `std::nullptr_t`, který lze převést na libovolný nezpracovaný typ ukazatele.  I když lze použít klíčové slovo **nullptr** bez zahrnutí hlaviček, pokud váš kód používá typ `std::nullptr_t`, je nutné jej definovat zahrnutím `<cstddef>`záhlaví.

> [!NOTE]
>  Klíčové slovo **nullptr** je také definováno v C++/CLI pro aplikace spravovaného kódu a není zaměnitelné s klíčovým slovem standard C++ ISO. Pokud váš kód může být zkompilován pomocí možnosti kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , která cílí na spravovaný kód, pak použijte `__nullptr` v jakémkoli řádku kódu, kde je nutné zaručit, že kompilátor používá nativní C++ výklad. Další informace naleznete v tématu [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Poznámky

Vyhněte se použití hodnoty NULL nebo nuly (`0`) jako konstanty ukazatele s hodnotou null; u **nullptr** je méně zranitelná na zneužití a ve většině případů funguje lépe.  Například zadání `func(std::pair<const char *, double>)` a následné volání `func(std::make_pair(NULL, 3.14))` způsobí chybu kompilátoru.  Makro NULL se rozbalí na `0` tak, aby volání `std::make_pair(0, 3.14)` vrátilo `std::pair<int, double>`, který nelze převést na typ parametru `std::pair<const char *, double>` func().  Volání `func(std::make_pair(nullptr, 3.14))` je úspěšně zkompilováno, protože `std::make_pair(nullptr, 3.14)` vrátí `std::pair<std::nullptr_t, double>`, který lze převést na `std::pair<const char *, double>`.

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
