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
ms.openlocfilehash: 990c48a72c3f6017d893ddf9b46bcbb737bfb634
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820192"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (předběžné zpracování názvu výstupního souboru)

Určuje název výstupního souboru, do kterého [/P (předběžné zpracování souboru)](p-preprocess-to-a-file.md) – možnost kompilátoru zapíše Předzpracovaný výstup.

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

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[/P (předzpracování do souboru)](p-preprocess-to-a-file.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
