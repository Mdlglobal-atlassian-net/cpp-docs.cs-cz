---
title: Používání příkazu abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187854"
---
# <a name="using-abort"></a>Používání příkazu abort

Zavoláním funkce [Abort](../c-runtime-library/reference/abort.md) dojde k okamžitému ukončení. Funkce obchází běžný proces ničení inicializovaných globálních statických objektů. Také obchází všechna speciální zpracování zadaná pomocí funkce `atexit`.

## <a name="see-also"></a>Viz také

[Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)
