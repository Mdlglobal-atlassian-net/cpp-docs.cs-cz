---
title: Robustnost
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 5e13152b2c31511cce4df9976d6c800960c099a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444889"
---
# <a name="robustness"></a>Robustnost

Použijte následující funkce běhové knihovny jazyka C ke zvýšení odolnosti programu.

## <a name="run-time-robustness-functions"></a>Funkce odolnosti za běhu

|Funkce|Použití|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Přenáší řízení do mechanismu zpracování chyb, pokud operátor **New** nedokáže přidělit paměť.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Zpracovává výjimky Win32 (strukturované výjimky jazyka C) C++ jako typové výjimky.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Nainstaluje svou vlastní funkci ukončení, která se má volat po [ukončení](../c-runtime-library/reference/terminate-crt.md).|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Nainstaluje vaši vlastní funkci ukončení, která se bude volat [neočekávaným](../c-runtime-library/reference/unexpected-crt.md).|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
