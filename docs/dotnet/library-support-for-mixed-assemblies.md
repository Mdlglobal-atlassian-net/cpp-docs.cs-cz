---
title: Podpora knihovny pro smíšená sestavení
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312005"
---
# <a name="library-support-for-mixed-assemblies"></a>Podpora knihovny pro smíšená sestavení

Visual C++ podporuje použití standardní knihovny C++, knihovny runtime jazyka C (CRT), ATL a MFC pro aplikace kompilované s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). To umožňuje existující aplikace, které používají tyto knihovny použít také funkce rozhraní .NET Framework.

> [!IMPORTANT]
> **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Tato podpora zahrnuje následující knihovny DLL a import:

- Lib Msvcmrt [d] Pokud kompilujete s **/CLR**. Smíšená sestavení odkaz na tuto knihovnu importu.

Tato podpora poskytuje že několik souvisejících výhody:

- CRT a standardní knihovny C++ jsou k dispozici pro smíšený kód. CRT a standardní knihovny C++ k dispozici nejsou ověřitelný; Nakonec se volání stále směrují do stejné CRT a standardní knihovny C++ používáte z nativního kódu.

- Správné jednotný zpracování výjimek v smíšená Image.

- Statická inicializace proměnných C++ ve smíšené imagí.

- Podpora pro proměnné na úrovni AppDomain a na úrovni jednotlivého procesu ve spravovaném kódu.

- Řeší problémy s zámek zavaděče, aplikovaná na smíšených knihoven DLL zkompilovány v aplikaci Visual Studio 2003 a starších verzích.

Kromě toho tato podpora představuje následující omezení:

- Je podporován pouze model CRT knihovny DLL pro kód zkompilovaný s **/CLR**. Neexistují žádné statické knihovny CRT, které podporují **/CLR** sestavení.

## <a name="see-also"></a>Viz také:

- [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
