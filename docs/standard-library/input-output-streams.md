---
title: Vstupní výstupní proudy
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 3d5344ede3a62375c4c8102d1fc39445518eb0c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455263"
---
# <a name="inputoutput-streams"></a>Vstupní/výstupní datové proudy

`basic_iostream`, který je definován v hlavičkovém souboru \<IStream >, je šablona třídy pro objekty, které zpracovávají vstupní i výstupní datové proudy vstupně-výstupních znaků.

Existují dva definice typedefy `basic_iostream` , které definují specializace specifické pro znaky a mohou usnadnit čtení kódu: `iostream` (Nezaměňujte se souborem \<hlaviček iostream – >) je vstupně-výstupní proud, který je založen na `basic_iostream<char>`. je vstupně-výstupní proud, který je založen na `basic_iostream<wchar_t>`. `wiostream`

Další informace naleznete v tématu [Třída basic_iostream](../standard-library/basic-iostream-class.md), [iostream –](../standard-library/basic-iostream-class.md)a [wiostream](../standard-library/basic-iostream-class.md).

Odvození z `basic_iostream` je šablona `basic_fstream`třídy, která se používá ke streamování znakových dat do a ze souborů.

Existují také definice typedef, které poskytují specializace specifické pro jednotlivé znakové `basic_fstream`sady. Jsou `fstream`to, jedná se o datový proud v/v souboru, který je založen na typu `wfstream` **char**a, což je datový proud v/v souboru, který je založen na **wchar_t**. Další informace naleznete v tématu [Třída basic_fstream](../standard-library/basic-fstream-class.md), [fstream –](../standard-library/basic-fstream-class.md)a [wfstream](../standard-library/basic-fstream-class.md). Použití těchto definice typedef vyžaduje zahrnutí hlavičkového souboru \<fstream – >.

> [!NOTE]
> Když se pro vstup/výstup souboru použije objekt,přestožepodkladovávyrovnávacípaměťobsahujesamostatněurčenépozicepročteníazápis,aktuálnívstupníaaktuálnívýstupnípozicejsouvzájemněvázané,aprotočteníněkterýchdatpřesune`basic_fstream` výstupní pozice.

Šablona `basic_stringstream` třídy a její společná `stringstream`specializace jsou často používány pro práci s objekty vstupně-výstupních proudů pro vkládání a extrahování znakových dat. Další informace naleznete v tématu [Třída basic_stringstream](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Viz také:

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream – třída](../standard-library/basic-stringstream-class.md)\
[\<sstream >](../standard-library/sstream.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
