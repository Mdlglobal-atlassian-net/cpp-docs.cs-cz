---
title: Upozornění linkerů LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183420"
---
# <a name="linker-tools-warning-lnk4086"></a>Upozornění linkerů LNK4086

EntryPoint ' function ' není __stdcall s ' Number ' bajtů argumentů; Image se možná nespustí.

Vstupní bod pro knihovnu DLL musí být `__stdcall`. Buď znovu zkompilujte funkci s možností [/GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) , nebo zadejte `__stdcall` nebo WinAPI při definování funkce.
