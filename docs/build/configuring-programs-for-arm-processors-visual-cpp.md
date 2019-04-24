---
title: Konfigurace projektů C++ pro procesory ARM
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 7e6e0c97245c0941abc49096d1693a8d152c1709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273825"
---
# <a name="configure-c-projects-for-arm-processors"></a>Konfigurace projektů C++ pro procesory ARM

Tato část dokumentace obsahuje informace o tom, jak pomocí nástrojů sestavení MSVC cílit na ARM hardwaru.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled konvencí ARM ABI](overview-of-arm-abi-conventions.md)<br/>
Popisuje binárním rozhraním aplikace používá Windows na ARM pro využití registrů, konvence volání a zpracování výjimek.

[Přehled konvencí ARM64 ABI](arm64-windows-abi-conventions.md)<br/>
Popisuje binárním rozhraním aplikace používá Windows pro ARM64 pro využití registrů, konvence volání a zpracování výjimek.

[Běžné problémy s migrací ARM v prostředí MSVC](common-visual-cpp-arm-migration-issues.md)<br/>
Popisuje prvky kódu jazyka C++, které jsou obvykle považovány za přenosné mezi architekturami, ale které ARM než x86 a x64 produkují jiné výsledky.

[Zpracování výjimek ARM](arm-exception-handling.md)<br/>
Popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek v Windows na ARM zásobníku.

[Ošetření výjimek ARM64](arm64-exception-handling.md)<br/>
Popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek ve Windows pro ARM64 zásobníku.

## <a name="related-sections"></a>Související oddíly

[ARM – vnitřní prvky](../intrinsics/arm-intrinsics.md)<br/>
Popisuje kompilátor vnitřních objektů pro procesory, které používají architekturu ARM.
