---
title: Používání příkazu abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: e8cc7bce552acf67c0f9bf2025e0040dc051cff6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446412"
---
# <a name="using-abort"></a>Používání příkazu abort

Zavoláním funkce [Abort](../c-runtime-library/reference/abort.md) dojde k okamžitému ukončení. Funkce obchází běžný proces ničení inicializovaných globálních statických objektů. Také obchází všechna speciální zpracování zadaná pomocí funkce `atexit`.

## <a name="see-also"></a>Viz také

[Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)