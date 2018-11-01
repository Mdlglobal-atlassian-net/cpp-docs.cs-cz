---
title: /Fi (předběžné zpracování názvu výstupního souboru)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: d4de722ad33a9c9e5e7c37176bbe5d7031b68a39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450177"
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