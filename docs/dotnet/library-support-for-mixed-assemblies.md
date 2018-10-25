---
title: Podpora knihovny pro smíšená sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8c3fec26f3e41c3edd2346ac2e1b9b1f6b98ba33
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069617"
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
