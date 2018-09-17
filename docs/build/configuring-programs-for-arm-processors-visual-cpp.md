---
title: Konfigurace Visual C++ pro procesory ARM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce0e7e1f7c0936daed0fa6a51f6e254403205e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714958"
---
# <a name="configure-visual-c-for-arm-processors"></a>Konfigurace Visual C++ pro procesory ARM

Tato část dokumentace obsahuje informace o tom, jak cílit na ARM hardwaru pomocí nástroje pro sestavení Visual C++.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled konvencí ARM ABI](../build/overview-of-arm-abi-conventions.md) popisuje binárním rozhraním aplikace používá Windows na ARM pro využití registrů, konvence volání a zpracování výjimek.

[Přehled konvencí ABI ARM64](../build/arm64-windows-abi-conventions.md) popisuje binárním rozhraním aplikace používá Windows pro ARM64 pro využití registrů, konvence volání a zpracování výjimek.

[Běžné Visual C++ ARM problémy s migrací](../build/common-visual-cpp-arm-migration-issues.md) C++ popisuje prvky kódu, které jsou obvykle považovány za přenosné mezi architekturami, ale které ARM než x86 a x64 produkují jiné výsledky.

[Zpracování výjimek ARM](../build/arm-exception-handling.md) popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek v Windows na ARM zásobníku.

[Zpracování výjimek, ARM64](../build/arm64-exception-handling.md) popisuje schéma kódování pro uvolnění při zpracování strukturovaných výjimek v Windows pro ARM64 zásobníku.

## <a name="related-sections"></a>Související oddíly

[Vnitřní objekty ARM](../intrinsics/arm-intrinsics.md) popisuje kompilátor vnitřních objektů pro procesory, které používají architekturu ARM.
