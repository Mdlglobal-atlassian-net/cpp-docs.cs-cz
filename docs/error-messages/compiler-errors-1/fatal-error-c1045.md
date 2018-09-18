---
title: Závažná chyba C1045 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1045
dev_langs:
- C++
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c18d6f9b502e818992097c3042689cf66457792
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024772"
---
# <a name="fatal-error-c1045"></a>Závažná chyba C1045

limit kompilátoru: Specifikace propojení jsou vnořené moc hluboko

Vnořené externí typy překročit omezení kompilátoru. Vnořené externí typy jsou povolené s typem vnější propojení, jako například `extern` "C++". Snižte počet vnořených externích typů tuto chybu napravíme.