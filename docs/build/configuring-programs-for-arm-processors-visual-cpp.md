---
title: Konfigurace Visual C++ pro procesory ARM
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 9238bf9342984e788d3abe6d7da8b0974a78ac24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594217"
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurace Visual C++ pro procesory ARM

Tato část dokumentace obsahuje informace o tom, jak cílit na ARM hardwaru pomocí nástroje pro sestavení Visual C++.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md)<br/>
Popisuje binárním rozhraním aplikace používá Windows na ARM pro využití registrů, konvence volání a zpracování výjimek.

[Přehled konvencí ARM64 ABI](../build/arm64-windows-abi-conventions.md)<br/>
Popisuje binárním rozhraním aplikace používá Windows pro ARM64 pro využití registrů, konvence volání a zpracování výjimek.

[Běžné problémy s migrací ARM v prostředí Visual C++](../build/common-visual-cpp-arm-migration-issues.md)<br/>
Popisuje prvky kódu jazyka C++, které jsou obvykle považovány za přenosné mezi architekturami, ale které ARM než x86 a x64 produkují jiné výsledky.

[Zpracování výjimek ARM](../build/arm-exception-handling.md)<br/>
Popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek v Windows na ARM zásobníku.

[Ošetření výjimek ARM64](../build/arm64-exception-handling.md)<br/>
Popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek ve Windows pro ARM64 zásobníku.

## <a name="related-sections"></a>Související oddíly

[ARM – vnitřní prvky](../intrinsics/arm-intrinsics.md)<br/>
Popisuje kompilátor vnitřních objektů pro procesory, které používají architekturu ARM.
