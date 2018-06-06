---
title: Podpora knihovny pro smíšená sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: d4b584e0bacb1cb93cad33efdff807bb5fa9c8e2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704108"
---
# <a name="library-support-for-mixed-assemblies"></a>Podpora knihovny pro smíšená sestavení

Podporuje použití standardní knihovny C++, běhové knihovny jazyka C (CRT), Visual C++ ATL a MFC pro aplikace, kompilovat s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). To umožňuje existující aplikace, které používají tyto knihovny používat taky funkce rozhraní .NET Framework.

> [!IMPORTANT]
> **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Tato podpora zahrnuje následující knihovny DLL a import:

- Msvcmrt [d] .lib pokud kompilujete s **/CLR**. Smíšená sestavení odkaz na tuto knihovnu importu.

Tato podpora zajišťuje několik souvisejících výhod:

- CRT a standardní knihovny C++ jsou k dispozici pro smíšený kód. CRT a standardní knihovny C++ poskytuje nejsou ověřitelný; Nakonec voláními stále směrují stejné CRT a standardní knihovny C++ jako používáte z nativního kódu.

- Opravte jednotná zpracování výjimek ve smíšeném bitové kopie.

- Statické inicializace proměnných C++ ve smíšeném bitové kopie.

- Podpora pro proměnné na AppDomain a na proces ve spravovaném kódu.

- Řešení problémů zámek zavaděče použité smíšených knihoven DLL kompilovat v aplikaci Visual Studio 2003 a starších verzích.

Kromě toho tato podpora představuje následující omezení:

- Pro kód kompilovat s je podporován pouze model knihovny DLL CRT **/CLR**. Neexistují žádné statické knihovny CRT, které podporují **/CLR** sestavení.

Common language runtime (CLR) by měl aktualizovat na aktuální verzi jako není zaručena pro práci s předchozími verzemi. Kód vytvořené s nástroji tyto změny se nespustí na verze CLR 1.x.

## <a name="see-also"></a>Viz také:

- [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
