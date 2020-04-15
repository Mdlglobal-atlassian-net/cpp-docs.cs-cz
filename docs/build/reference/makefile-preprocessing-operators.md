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
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336475"
---
# <a name="makefile-preprocessing-operators"></a>Operátory předběžného zpracování souboru pravidel

Výrazy předběžného zpracování makefile mohou používat operátory, které fungují s konstantními hodnotami, ukončovacími kódy z příkazů, řetězců, maker a cest systému souborů. Chcete-li vyhodnotit výraz, preprocesor nejprve rozbalí makra a potom provede příkazy a poté provede operace. Operace jsou vyhodnocovány v pořadí explicitní seskupení v závorky a potom v pořadí priority operátoru. Výsledkem je konstantní hodnota.

Operátor **DEFINED** je logický operátor, který funguje s názvem makra. Výraz **DEFINED(**_macroname_**)** je true, pokud je definován název *makra,* i když nemá přiřazenou hodnotu. **DEFINOVÁNO** v kombinaci s **! POKUD** nebo **! ELSE IF** je ekvivalentní **! IFDEF** nebo **! ELSE IFDEF**. Však na rozdíl od těchto směrnic **DEFINED lze** použít ve složitých výrazů.

Operátor **EXIST** je logický operátor, který pracuje na cestě systému souborů. **EXIST(**_cesta)_**)** je true, pokud *cesta* existuje. Výsledek z **EXIST** lze použít v binárních výrazech. Pokud *cesta* obsahuje mezery, uzavřete ji do uvozovek.

Chcete-li porovnat dva řetězce,**==** použijte operátor rovnosti ( ) nebo operátor nerovnosti (**!=**). Řetězce uzavřete do uvozovek.

Celé konstanty mohou používat unární operátory pro číselné negace**-****~**( ), jeden doplněk ( ), a logické negace (**!**).

Výrazy můžete použít následující operátory. Operátory se stejnou prioritou jsou seskupeny a skupiny jsou uvedeny v sestupném pořadí podle priority. Unární operátory přidružit k operandu vpravo. Binární operátory se stejnou prioritou přidruží operandy zleva doprava.

|Operátor|Popis|
|--------------|-----------------|
|**DEFINED(** *makronázev* **)**|Vytvoří logickou hodnotu pro aktuální definiční stav *názvu makra*.|
|**EXIST(** *cesta* **)**|Vytvoří logickou hodnotu pro existenci souboru na *cestě*.|
|||
|**!**|Unární logické NOT.|
|**~**|Unární jeden doplněk.|
|**-**|Unární negace.|
|||
|**&#42;**|Násobení.|
|**/**|Divize.|
|**%**|Modul (zbytek).|
|||
|**+**|Kromě toho.|
|**-**|Odčítání.|
|||
|**\<\<**|Bitový posun doleva.|
|**>>**|Bitový posun doprava.|
|||
|**\<=**|Menší nebo rovno.|
|**>=**|Větší než nebo rovno.|
|**\<**|Méně než.|
|**>**|Větší než.|
|||
|**==**|Rovnosti.|
|**!=**|Nerovnost.|
|||
|**&**|Bitové AND.|
|**^**|Bitové XOR.|
|**&#124;**|Bitové NEBO.|
|||
|**&&**|Logické and.|
|||
|**&#124;&#124;**|Logické OR.|

> [!NOTE]
> Bitový operátor XOR**^**( ) je stejný jako řídicí znak **^^** a musí být uvozen (jako ) při použití ve výrazu.

## <a name="see-also"></a>Viz také

- [Výrazy v předběžném zpracování souboru pravidel](expressions-in-makefile-preprocessing.md)
