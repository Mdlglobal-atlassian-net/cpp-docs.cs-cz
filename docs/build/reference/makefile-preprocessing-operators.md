---
title: Operátory předběžného zpracování souboru pravidel
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 2276f6a3c28c6f2fac509ef0e4bc14cce9932582
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170460"
---
# <a name="makefile-preprocessing-operators"></a>Operátory předběžného zpracování souboru pravidel

Výrazy předběžného zpracování souboru pravidel můžou používat operátory, které se chovají na konstantních hodnotách, ukončovací kódy z příkazů, řetězců, maker a cest k systémům souborů. Pro vyhodnocení výrazu preprocesor nejprve rozbalí makra a pak provede příkazy a pak provede operace. Operace se vyhodnocují v pořadí explicitního seskupení v závorkách a potom v pořadí podle priority operátora. Výsledkem je konstantní hodnota.

**Definovaný** operátor je logický operátor, který funguje s názvem makra. Výraz **definovaný (** _název_makra_ **)** má hodnotu true, pokud je definován *název_makra* , i v případě, že nemá přiřazenou hodnotu. **Definováno** v kombinaci s **! Pokud** nebo **! JINAK, pokud** je ekvivalentem **! IFDEF** nebo **! JINAK IFDEF**. Nicméně na rozdíl od těchto direktiv lze **definovat** použít ve složitých výrazech.

Operátor **existing** je logický operátor, který funguje na cestě k systému souborů. Existuje **(** _cesta_ **)** má hodnotu true, pokud *cesta* existuje. Výsledek z **existence** lze použít v binárních výrazech. Pokud *cesta* obsahuje mezery, uzavřete ji do dvojitých uvozovek.

Chcete-li porovnat dva řetězce, použijte operátor rovnosti ( **==** ) nebo operátor nerovnosti ( **! =** ). Uzavřete řetězce do dvojitých uvozovek.

Celočíselné konstanty mohou používat unární operátory pro číselnou negaci ( **-** ), jeden doplněk ( **~** ) a logickou negaci ( **!** ).

Výrazy mohou používat následující operátory. Operátory stejné priority jsou seskupeny dohromady a skupiny jsou uvedeny v sestupném pořadí podle priority. Unární operátory jsou spojeny s operandem vpravo. Binární operátory stejné priority přiřadí operandy zleva doprava.

|Operátor|Popis|
|--------------|-----------------|
|**Definováno (** *název_makra* **)**|Vytvoří logickou hodnotu pro aktuální stav definice *název_makra*.|
|**Existují (** *cesta* **)**|Vytvoří logickou hodnotu pro existenci souboru v *cestě*.|
|||
|**!**|Unární logický operátor NOT.|
|**~**|Unární doplněk.|
|**-**|Unární negace.|
|||
|**&#42;**|Násobení.|
|**/**|Dělení.|
|**%**|Zbytek (zbytek).|
|||
|**+**|Přidání.|
|**-**|Odčítání.|
|||
|**\<\<**|Bitový posun vlevo.|
|**>>**|Bitový posun vpravo.|
|||
|**\<=**|Je menší nebo rovno.|
|**>=**|Je větší nebo rovno.|
|**\<**|Je menší než.|
|**>**|Větší než.|
|||
|**==**|Porovnávání.|
|**!=**|Nerovnost.|
|||
|**&**|Bitový AND.|
|**^**|Bitový operátor XOR.|
|**&#124;**|Bitový operátor OR.|
|||
|**&&**|Logický operátor AND.|
|||
|**&#124;&#124;**|Logický operátor OR.|

> [!NOTE]
> Bitový operátor XOR ( **^** ) je stejný jako řídicí znak a musí být uvozena řídicím znakem (jako **^^** ) při použití ve výrazu.

## <a name="see-also"></a>Viz také

- [Výrazy v předběžném zpracování souboru pravidel](expressions-in-makefile-preprocessing.md)
