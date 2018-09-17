---
title: Import do aplikace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- importing DLLs [C++], applications
- applications [C++], importing into
ms.assetid: 9d646466-e12e-4710-8ad9-c819c0375fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88d34ce685e22e561683cc33db25997650ed7fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718380"
---
# <a name="importing-into-an-application"></a>Import do aplikace

Funkce můžete importovat do aplikace pomocí dvou metod:

- Pomocí klíčových slov **__declspec(dllimport)** v definici funkce v hlavní aplikaci

- Pomocí souboru modulu definice (.def) společně s **deklarace __declspec(dllimport)**

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Import volání funkcí pomocí deklarace __declspec(dllimport)](../build/importing-function-calls-using-declspec-dllimport.md)

- [Import dat pomocí deklarace __declspec(dllimport)](../build/importing-data-using-declspec-dllimport.md)

- [Import pomocí souborů DEF](../build/importing-using-def-files.md)

## <a name="see-also"></a>Viz také

[Import a export](../build/importing-and-exporting.md)