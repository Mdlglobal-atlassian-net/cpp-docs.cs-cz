---
title: Zpracování výjimek (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: 9f5662bb9e744b5db3b0ab25ac4230b2f67016bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182120"
---
# <a name="exception-handling--ccli-and-ccx"></a>Zpracování výjimek (C++/CLI a C++/CX)

Aplikace zkompilované pomocí možnosti kompilátoru `/ZW` nebo `/clr` kompilátoru používají *výjimky* ke zpracování neočekávaných chyb během provádění programu. Následující témata popisují zpracování výjimek v aplikacích C++/CX nebo C++/CLI.

## <a name="in-this-section"></a>V tomto oddílu

[Základní koncepty při práci se spravovanými výjimkami](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Popisuje vyvolávání výjimek a použití bloku **try**/**catch** .

[Rozdíly v chování zpracování výjimek v rámci/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Popisuje rozdíly oproti standardnímu chování zpracování C++ výjimek.

[finally](../dotnet/finally.md)<br/>
Popisuje způsob použití klíčového slova finally.

[Postupy: Definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Ukazuje, jak lze zachytit neošetřené výjimky.

[Postupy: Zachycení výjimek v nativním kódu z prostředí MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Popisuje, jak zachytit CLR a C++ výjimky v nativním kódu.

[Postupy: Definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Ukazuje, jak zachytit všechny neošetřené výjimky.

## <a name="related-sections"></a>Související oddíly

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
Popisuje zpracování výjimek ve standardu C++.

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
