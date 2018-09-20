---
title: Zpracování výjimek (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2213266d281933c6a6a59775584532acaeb39d6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412315"
---
# <a name="exception-handling--c-component-extensions"></a>Zpracování výjimek (rozšíření komponent C++)

Zkompilovaná aplikace `/ZW` – možnost kompilátoru nebo `/clr` – možnost kompilátoru používají *výjimky* zpracování neočekávaných chyb během provádění programu. Následující témata popisují zpracování výjimek v obou C + +/ CX nebo C + +/ CLI aplikací.

## <a name="in-this-section"></a>V tomto oddílu

[Základní koncepty při práci se spravovanými výjimkami](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Popisuje generování výjimek a pomocí **zkuste**/**catch** bloky.

[Rozdíly v chování zpracování výjimek v/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Tento článek popisuje rozdíly oproti standardní chování zpracování výjimek jazyka C++.

[finally](../dotnet/finally.md)<br/>
Tento článek popisuje způsob použití finally – klíčové slovo.

[Postupy: Definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Ukazuje, jak neošetřené výjimky mohou být zachyceny.

[Postupy: Zachycení výjimek v nativním kódu z prostředí MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Popisuje, jak zachytávat výjimky CLR a C++ v nativním kódu.

[Postupy: Definování a instalace globální obslužné rutiny výjimek](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Ukazuje, jak zachytit všechny neošetřené výjimky.

## <a name="related-sections"></a>Související oddíly

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
Popisuje zpracování výjimek v C++.

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)