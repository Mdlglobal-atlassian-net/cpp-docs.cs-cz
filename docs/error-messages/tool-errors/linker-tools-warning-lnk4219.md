---
title: Upozornění linkerů LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410249"
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219

Oprava název opravou přetečení. Cílový "název symbolu cíl" je mimo rozsah. vkládá se převodní rutina

Linker vloží převodní rutina v situaci, kdy se nepodařilo přizpůsobit do uvedené instrukce, protože cílový symbol je příliš daleko od umístění instrukce adresy nebo posun.

Možná budete chtít změnit pořadí bitovou kopii (pomocí [/ORDER](../../build/reference/order-put-functions-in-order.md) volby, například), aby úroveň dereference.