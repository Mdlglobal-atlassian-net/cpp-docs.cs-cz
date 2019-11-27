---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: b7344d9cb685e0212748d7835e19f398f14979e7
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74393726"
---
# <a name="segment"></a>SEGMENT

Definuje segment programu *s názvem, který má atributy* segmentů.

## <a name="syntax"></a>Syntaxe

> *Name* **segment** ⟦**jen pro čtení**⟧ ⟦*align*⟧ ⟦*kombinovat*⟧ ⟦*použití*⟧ ⟦*charakteristiky*⟧ **alias (** _String_ **)** ⟦ __'__ *Class* __'__ ⟧ \
> \ *příkazů*
> **konec** názvu

#### <a name="parameters"></a>Parametry

*align*<br/>
Rozsah adres paměti, ze kterých lze vybrat počáteční adresu segmentu. Typ zarovnání může být jeden z následujících:

|Typ zarovnání|Počáteční adresa|
|----------------|----------------------|
|**BYTOVÉ**|Další dostupná bajtová adresa.|
|**WORD**|Další dostupná adresa slova (2 bajty na slovo).|
|**DWORD**|Další dostupná adresa dvojitého slova (4 bajty na jeden typ Word).|
|**–**|Další dostupná adresa odstavce (16 bajtů za odstavec).|
|**PAGE**|Další adresa stránky k dispozici (256 bajtů na stránku).|
|**Zarovnat**(*n*)|Další dostupná *n*-tou bajtová adresa Další informace najdete v části poznámky.|

Pokud tento parametr nezadáte, použije se ve výchozím nastavení **para** .

*kombinovat*\
**Veřejné**, **zásobník**, **běžné**, **paměť**, **na**<em>adrese</em>, **soukromá**

*použít*\
**USE16**, **USE32**, **plochý**

\ *charakteristik*
**Informace**, **čtení**, **zápis**, **spouštění**, **sdílení**, **ukládání do mezipaměti**a **zahození**

Jsou podporovány pouze pro COFF a odpovídají charakteristikám oddílu COFF podobného názvu (například **Shared** odpovídá IMAGE_SCN_MEM_SHARED). ČTENÍ nastaví příznak IMAGE_SCN_MEM_READ. Neplatný příznak jen pro čtení způsobil, že oddíl IMG_SCN_MEM_WRITE příznak pro vymazání. Pokud jsou nastaveny jakékoli *charakteristiky* , výchozí vlastnosti se nepoužijí a uplatní se jenom ty příznaky, které jsou v něm zadané.

\ _řetězců_
Tento řetězec se používá jako název oddílu ve vygenerovaném objektu COFF.  Vytvoří více oddílů se stejným externím názvem s odlišnými názvy segmentů MASM.

Nepodporováno v **/OMF**.

\ *třídy*
Určuje, jak mají být segmenty kombinovány a uspořádány v sestaveném souboru. Typické hodnoty jsou, `'DATA'`, `'CODE'`, `'CONST'` a `'STACK'`

## <a name="remarks"></a>Poznámky

Pro `ALIGN(n)`může být *n* jakákoli mocnina 2 od 1 do 8192. Nepodporováno v **/OMF**.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
