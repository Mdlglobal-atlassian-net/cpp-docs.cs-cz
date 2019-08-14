---
title: Závažná chyba nástroje NMAKE U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980535"
---
# <a name="nmake-fatal-error-u1045"></a>Závažná chyba nástroje NMAKE U1045

> Vytvoření se nezdařilo: *zpráva*

Program nebo příkaz, který se v nástroji NMAKE nezdařil z důvodu ve *zprávě*. Když NMAKE volá jiný program, například kompilátor nebo linker, volání může selhat. Nebo je možné, že volaný program vrátí chybu. Tato zpráva se používá k nahlášení chyby.

Chcete-li tento problém vyřešit, je třeba nejprve určit příčinu chyby. Pomocí příkazů, které jsou hlášeny pomocí možnosti NMAKE [/n](../../build/reference/running-nmake.md#nmake-options) , můžete ověřit nastavení prostředí a opakovat akce provedené nástrojem NMAKE na příkazovém řádku.
