---
title: 2.4 konstrukce pro sdílení práce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411115"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukce pro sdílení práce

Konstruktoru work-sharing distribuuje provádění asociovaný příkaz mezi členy týmu, na které ho. Direktiv pro sdílení práce nespouštět nová vlákna a neexistuje žádný implicitní bariéry při vstupu do konstruktoru work-sharing.

Vytvoří posloupnost sdílení práce a **bariéry** direktivy došlo k musí být stejná pro každé vlákno v týmu.

OpenMP – definuje následující konstrukce pro sdílení práce, a tyto možnosti jsou popsány v následující části:

- **pro** – direktiva

- **oddíly** – direktiva

- **jeden** – direktiva