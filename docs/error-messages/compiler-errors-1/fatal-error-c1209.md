---
title: Závažná chyba C1209 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1209
dev_langs:
- C++
helpviewer_keywords:
- C1209
ms.assetid: aa9ee10f-abe3-4683-9792-adca4cbbabb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e518cacdeb8db133ff6378e6569ee868312b8333
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081491"
---
# <a name="fatal-error-c1209"></a>Závažná chyba C1209

Sestavení Friend nejsou podporovaná ve verzi modulu runtime nainstalovaný

C1208 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

Pokud chcete vyřešit C1209, nainstalujte modul common language runtime, dodávané s kompilátorem, který používáte.

Další informace najdete v tématu [přátelská sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).