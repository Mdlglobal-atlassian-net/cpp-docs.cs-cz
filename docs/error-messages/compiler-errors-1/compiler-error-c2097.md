---
title: Chyba kompilátoru C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: cdb14aeef61d136a6992a05a72f382e589e88770
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207491"
---
# <a name="compiler-error-c2097"></a>Chyba kompilátoru C2097

Neplatná inicializace

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Inicializace proměnné pomocí nekonstantní hodnoty.

1. Inicializace krátké adresy s dlouhou adresou.

1. Inicializace místní struktury, sjednocení nebo pole s nekonstantním výrazem při kompilování s **/za**.

1. Inicializuje s výrazem, který obsahuje operátor čárky.

1. Inicializace s výrazem, který není konstanta ani symbolické.
