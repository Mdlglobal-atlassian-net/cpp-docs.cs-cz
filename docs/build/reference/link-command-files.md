---
title: Soubory příkazů LINK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8934758d8aa406ea7b7c959b1fc535cde32195b1
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894678"
---
# <a name="link-command-files"></a>Soubory příkazů LINK

Můžete předat argumenty příkazového řádku na odkaz ve formě souboru příkazů. K určení souboru příkazů do propojovacího programu, použijte následující syntaxi:

> **ODKAZ \@**  <em>commandfile</em>

*Commandfile* je název textového souboru. Je povolená žádná mezera nebo tabulátor mezi zavináč (**\@**) a název souboru. Neexistuje žádný výchozí příponou; je nutné zadat úplný název souboru, včetně všech rozšíření. Zástupné znaky nelze použít. Můžete zadat absolutní nebo relativní cestu s názvem. ODKAZ nepoužívá proměnnou prostředí k vyhledání souboru.

V souboru příkazů, argumentů je možné oddělit mezerami či tabulátory (jako v příkazovém řádku) a znaky nového řádku.

Můžete zadat část nebo celý příkazový řádek v souboru příkazů. Můžete použít více než jeden soubor příkazů v příkazu LINK. ODKAZ přijímá vstup souboru příkazů, jako kdyby byly zadány v dané oblasti na příkazovém řádku. Soubory příkazů nelze vnořit. ODKAZ vypisuje obsah soubory příkazů, pokud [/nologo](../../build/reference/nologo-suppress-startup-banner-linker.md) je zadána možnost.

## <a name="example"></a>Příklad

Následující příkaz pro vytvoření knihovny DLL předá názvy souborů objektů a knihoven v souborech samostatných příkazů a používá třetí příkaz specifikace možnost/EXPORTS v souboru:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)