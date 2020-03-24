---
title: Závažná chyba nástroje NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182692"
---
# <a name="nmake-fatal-error-u1073"></a>Závažná chyba nástroje NMAKE U1073

Nevím, jak vytvořit cílový_název

Zadaný cíl neexistuje a není k dispozici žádný příkaz ke spuštění nebo odvození pravidla.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Zkontrolujte pravopis cílového názvu.

1. Pokud je *TargetName* typu pseudotarget, zadejte ho jako cíl v jiném bloku Description.

1. Pokud je *TargetName* voláním makra, ujistěte se, že se nerozšíří na řetězec s hodnotou null.
