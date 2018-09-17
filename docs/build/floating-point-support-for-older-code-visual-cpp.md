---
title: Podpora plovoucí desetinné čárky starším kódu (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7285325bf1a934afcef337da318d019ec6fe375c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706807"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Podpora plovoucí desetinné čárky ve starším kódu (Visual C++)

MMX a registry zásobníku s plovoucí desetinnou čárkou (MM0-MM7/ST0-ST7) jsou zachovány v kontextu.  Neexistuje žádné explicitní konvenci volání pro tyto registry.  Použití těchto registrů je přísně zakázáno v kódu v režimu jádra.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)