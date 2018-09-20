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
ms.openlocfilehash: fbdf882367deb34570dd5b5ebb1b4001be739297
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373854"
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
