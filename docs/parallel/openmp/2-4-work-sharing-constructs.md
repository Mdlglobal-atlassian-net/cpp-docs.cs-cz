---
title: 2.4 Konstrukce pro sdílení práce
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502879"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukce pro sdílení práce

Konstruktoru work-sharing distribuuje provádění asociovaný příkaz mezi členy týmu, na které ho. Direktiv pro sdílení práce nespouštět nová vlákna a neexistuje žádný implicitní bariéry při vstupu do konstruktoru work-sharing.

Vytvoří posloupnost sdílení práce a **bariéry** direktivy došlo k musí být stejná pro každé vlákno v týmu.

OpenMP – definuje následující konstrukce pro sdílení práce, a tyto možnosti jsou popsány v následující části:

- **pro** – direktiva

- **oddíly** – direktiva

- **jeden** – direktiva