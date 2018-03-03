---
title: "partial (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd2debe47b0c60907c1a75f4e8b96d227468a345
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="partial--c-component-extensions"></a>partial (rozšíření komponent C++)
`partial` – Klíčové slovo umožňuje různé části stejnou třídu ref vytvářet nezávisle a v různých souborů.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Tato funkce jazyka platí pouze pro prostředí Windows Runtime).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Pro ref třídy, která má dva částečné definice `partial` – klíčové slovo se použije pro první výskyt definici, a to se obvykle provádí pomocí automaticky generovaného kódu, tak, aby lidské kodér nepoužívá velmi často klíčové slovo. Všechny následné částečné definice třídy, vynechejte `partial` modifikátor z *klíč třídy* – klíčové slovo a třída identifikátor. Když kompilátor narazí třídu dříve definovaném ref a identifikátor třídy, ale ne `partial` – klíčové slovo, interně kombinuje všechny části definice třídy ref do jednu definici.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
partial class-key identifier {  
   /* The first part of the partial class definition. 
      This is typically auto-generated */  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */  
}  
```  
  
### <a name="parameters"></a>Parametry  
 *klíč třídy*  
 Klíčové slovo, které deklaruje třídě nebo struktuře, která podporuje prostředí Windows Runtime. Buď `ref class`, `value class`, `ref struct`, nebo `value struct`.  
  
 *identifikátor*  
 Název definovaného typu.  
  
### <a name="remarks"></a>Poznámky  
 Částečné třídy podporuje scénáře, kde je upravit část definice třídy v jeden soubor a automatické generování kódu softwaru – například návrháře XAML – upraví kódu ve stejné třídě v jiném souboru. Pomocí konkrétní třídu, můžete zabránit generátor kódu automatické přepsal vašeho kódu. V projektu sady Visual Studio `partial` modifikátor automaticky generovaný soubor.  
  
 Obsah: Se dvěma výjimkami, definice částečné třídy může obsahovat všechny položky, které by mohly obsahovat definici úplné třídy, pokud `partial` – klíčové slovo byl vynechán. Však nelze zadat usnadnění – třída (například `public partial class X { ... };`), nebo `declspec`.  
  
 Specifikátory použít v definici třídu pro přístup k *identifikátor* neovlivní výchozí usnadnění v následných částečně nebo zcela – třída definice *identifikátor*. Definice vloženého členy statických dat jsou povoleny.  
  
 Deklarace: Částečnou definici třídy *identifikátor* pouze představuje název *identifikátor*, ale *identifikátor* nelze použít způsobem, který vyžaduje třídu definice. Název *identifikátor* nelze použít k vědět, velikost *identifikátor*, nebo použijte základní nebo člen *identifikátor* až po kompilátor narazí úplné definice *identifikátor*.  
  
 Počet a řazení: může být nula nebo víc definic třídu pro *identifikátor*. Každá definice třídu *identifikátor* musí předcházet lexikálně jednu úplnou definici *identifikátor* (Pokud je úplná definice; jinak hodnota třídy nelze použít s výjimkou jako předat dál deklarovaný), ale nemusí předcházet dopředného prohlášení o *identifikátor*. Všechny třídy klíče se musí shodovat.  
  
 Úplné definice: v místě úplné definice třídy *identifikátor*, toto chování je stejné jako definice *identifikátor* byl deklarován všechny základní třídy, členové atd. v pořadí, ve kterém by byly došlo a definované v částečné třídy.  
  
 Šablony: Částečné třídy nelze šablonu.  
  
 Obecné typy: Konkrétní třídu může být obecný, pokud je úplná definice může být obecný. Ale každá třída částečné a úplné musí obsahovat přesně stejnou obecné parametry, včetně názvů formální parametr.  
  
 Další informace o tom, jak používat `partial` – klíčové slovo, najdete v části [částečné třídy (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 (Tato funkce jazyka se nevztahuje na modul Common Language Runtime.)  
  
## <a name="see-also"></a>Viz také  
 [Částečné třídy (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)