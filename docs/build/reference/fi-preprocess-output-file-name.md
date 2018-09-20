---
title: -Fi (předběžné zpracování názvu výstupního souboru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f69a4ab16956924e3bcfd785c6a86c7ac238b36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431551"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (předběžné zpracování názvu výstupního souboru)

Určuje název výstupního souboru, do kterého [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru zapíše Předzpracovaný výstup.

## <a name="syntax"></a>Syntaxe

```
/Fipathname
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`pathname`|Název a cesta k výstupní soubor vytvářených **/P** – možnost kompilátoru.|

## <a name="remarks"></a>Poznámky

Použití **/Fi** – možnost kompilátoru v kombinaci s **/P** – možnost kompilátoru.

Pokud zadáte pouze cestu `pathname` parametr, základní název zdrojového souboru se používá jako základní název předzpracovaného výstupního souboru. `pathname` Parametr nevyžaduje konkrétní příponu. Pokud nezadáte příponu názvu souboru se ale používá rozšíření ".i".

## <a name="example"></a>Příklad

Následující příkaz upraví PROGRAM.cpp, zachová komentáře, přidá [#line](../../preprocessor/hash-line-directive-c-cpp.md) direktivy a zapíše výsledek do souboru MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[/P (předzpracování do souboru)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)