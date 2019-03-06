---
title: Práce s importovanými knihovnami a exportovanými soubory
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: fa759482d6949b27f5076643d83e92cddc1d8fac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416563"
---
# <a name="working-with-import-libraries-and-export-files"></a>Práce s importovanými knihovnami a exportovanými soubory

LIB se parametr/def slouží k vytvoření knihovny importu a souboru exportu. Exportuje používá odkaz vytvořit program, který obsahuje soubor exportu (obvykle dynamickou knihovnu (DLL)) a používá knihovnu importu přeložit odkazy na tyto exporty v jiných aplikacích.

Všimněte si, že když vytvoříte knihovny importu v předběžný krok před vytvořením vaší knihovny DLL, je nutné předat stejnou sadu souborů objektů při sestavování knihovny DLL, jako úspěšný při sestavování knihovny importu.

Ve většině případů není nutné používat k vytváření knihovny importu LIB. Při propojení programu (spustitelný soubor nebo knihovny DLL), který obsahuje exporty odkaz automaticky vytvoří knihovnu importu, který popisuje exporty. Později Když propojíte svůj program, který odkazuje na tyto exporty, zadejte knihovnu importu.

Ale pokud knihovna DLL exportuje do programu, který také importy z, určuje, zda přímo nebo nepřímo, musí používáte LIB vytvořit jeden z knihovny importu. Když LIB vytvoří knihovnu importu, také vytvoří soubor exportu. Při propojování jednu z knihoven DLL, je nutné použít souboru exportu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)
