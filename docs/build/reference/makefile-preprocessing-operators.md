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
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823120"
---
# <a name="makefile-preprocessing-operators"></a>Operátory předběžného zpracování souboru pravidel

Výrazy předběžného zpracování souboru pravidel, můžete použít operátory, které fungují na konstantní hodnoty, ukončovací kód z příkazů, řetězce, makra a cesty k systému souborů. Vyhodnotit výraz, preprocesor nejprve rozbalí makra a pak provede příkazy a pak provádí operace. Operace se vyhodnocují v pořadí explicitní seskupování v závorkách a potom v pořadí podle priority operátorů. Výsledkem je konstantní hodnota.

**Definované** operátor je logický operátor, který funguje na název makra. Výraz **definované (**_makro_**)** má hodnotu true Pokud *makro* je definován, i když nemá přiřazenou hodnotu. **DEFINOVANÉ** v kombinaci s **! Pokud** nebo **! ELSE IF** je ekvivalentní **! IFDEF** nebo **! OSTATNÍ IFDEF**. Ale na rozdíl od tyto direktivy **definované** lze použít v složité výrazy.

**Existují** operátor je logický operátor, který funguje na cestu systému souborů. **Existují (**_cesta_**)** má hodnotu true Pokud *cesta* existuje. Výsledek z **existují** lze použít v binární výrazy. Pokud *cesta* obsahuje mezery, uzavřete do dvojitých uvozovek.

Chcete-li porovnat dva řetězce, použijte rovnosti (**==**) operátor nebo nerovnost (**! =**) – operátor. Řetězce uzavřete do dvojitých uvozovek.

Konstanty typu Integer unární operátory lze použít pro numerické negace (**-**), jeden je doplňují (**~**) a Logická negace (**!**).

Výrazy můžete použít následující operátory. Operátory stejnou prioritu jsou seskupené dohromady a skupin jsou uvedeny v sestupném pořadí podle priority. Unární operátory jsou asociativní operandu vpravo. Binární operátory stejnou prioritu přidružit operandů zleva doprava.

|Operátor|Popis|
|--------------|-----------------|
|**DEFINOVANÉ (** *makro* **)**|Vytvoří logickou hodnotu pro aktuální stav definice *makro*.|
|**Existují (** *cesta* **)**|Vytvoří logickou hodnotu existence souboru lokality v *cesta*.|
|||
|**\!**|Unární logický operátor NOT.|
|**~**|Unární, jeden z doplňku.|
|**-**|Unární negace.|
|||
|**&#42;**|Násobení.|
|**/**|Dělení.|
|**%**|Modulo (zbytek).|
|||
|**+**|Přidání.|
|**-**|Odčítání.|
|||
|**\<\<**|Bitový Posun vlevo.|
|**>>**|Bitový Posun vpravo.|
|||
|**\<=**|Menší než nebo rovno.|
|**>=**|Větší než nebo rovno.|
|**\<**|Menší než.|
|**>**|Větší než.|
|||
|**==**|Rovnost.|
|**\!=**|Nerovnost.|
|||
|**&**|Bitový AND.|
|**^**|Bitový operátor XOR.|
|**&#124;**|Bitový operátor OR.|
|||
|**&&**|Logickým operátorem a.|
|||
|**&#124;&#124;**|Logický operátor OR.|

> [!NOTE]
> Bitový operátor XOR (**^**) je stejný jako řídicí znak a musí být uvozeny řídicími znaky (jako **^^**) Pokud je použit ve výrazu.

## <a name="see-also"></a>Viz také:

- [Výrazy v předběžném zpracování souboru pravidel](expressions-in-makefile-preprocessing.md)