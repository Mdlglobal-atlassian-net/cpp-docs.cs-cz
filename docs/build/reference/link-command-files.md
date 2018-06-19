---
title: Soubory příkazů LINK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6614af87f072c54353ead39c2c5ca789da18dbb8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375282"
---
# <a name="link-command-files"></a>Soubory příkazů LINK
Argumenty příkazového řádku můžete předat odkaz ve formě soubor příkazů. Chcete-li určit soubor příkazů do propojovacího programu, použijte následující syntaxi:  
  
```  
LINK @commandfile  
```  
  
 `commandfile` Je název textového souboru. Je povolen žádný místa nebo kartě mezi znaku zavináče (@) a název souboru. Neexistuje žádný výchozí rozšíření; je nutné zadat úplný název souboru, včetně všech rozšíření. Zástupné znaky nelze použít. Absolutní nebo relativní cestu můžete zadat název souboru. ODKAZ nepoužívá proměnné prostředí pro vyhledávání souboru.  
  
 V souboru příkaz argumenty můžete být odděleno mezerami nebo karty (jako na příkazovém řádku) a znaky nového řádku.  
  
 Můžete zadat nebo jeho část příkazového řádku v souboru příkaz. Můžete použít více než jeden soubor příkazů v příkazu odkaz. ODKAZ přijme vstupní soubor příkazů, jako kdyby byly zadány v tomto umístění na příkazovém řádku. Soubory příkazů nelze vnořit. ODKAZ vrátí obsah souborů příkaz, pokud [/nologo](../../build/reference/nologo-suppress-startup-banner-linker.md) je zadána možnost.  
  
## <a name="example"></a>Příklad  
 Následující příkaz pro vytvoření knihovny DLL předá názvy objekt soubory a knihovny v souborech samostatný příkaz a používá třetí příkaz soubor pro specifikaci volbou/EXPORTS:  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)