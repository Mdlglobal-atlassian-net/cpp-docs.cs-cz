---
title: "Obecná pravidla přetížení operátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 199db318eb847687d10044e0376b70c8d6d44feb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="general-rules-for-operator-overloading"></a>Obecná pravidla přetížení operátoru
Následující pravidla omezují způsob, jakým jsou implementovány přetížené operátory. Ale nelze je použít k [nové](../cpp/new-operator-cpp.md) a [odstranit](../cpp/delete-operator-cpp.md) operátory, které jsou popsané samostatně.  
  
-   Nelze definovat nové operátory, jako například **.  
  
-   Nelze předefinovat význam operátorů při použití předdefinovaných datových typů.  
  
-   Přetížené operátory musejí být členskými funkcemi nestatické třídy nebo globálními funkcemi. Globální funkce, která požaduje přístup k soukromým nebo chráněným členům, musí být pro danou třídu deklarována jako přátelská. Globální funkce musí přebírat alespoň jeden argument třídy nebo výčtového typu, případně odkazu na třídu nebo výčtový typ. Příklad:  
  
    ```  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     Předchozí příklad kódu deklaruje operátor „menší než“ jako členskou funkci. Operátory sčítání jsou však deklarovány jako globální funkce, které mají „přátelský“ přístup. Pro daný operátor může být poskytnuta více než jedna implementace. V případě předchozího operátoru sčítání jsou poskytnuty dvě implementace pro poskytnutí komutativity. Je to stejně pravděpodobné jako implementace operátorů, které sčítají `Point` s `Point`, `int` s `Point` atd.  
  
-   Operátory dodržují seskupování a respektují počet operandů zadaný jejich typickým použitím v rámci předdefinovaných typů. Proto neexistuje žádný způsob, jak express koncept "Přidat 2 a 3 na objekt typu `Point`," očekává 2, pokud chcete přidat do *x* souřadnice a 3, které mají být přidány do *y* koordinaci.  
  
-   Unární operátory, které jsou deklarovány jako členské funkce, nepřebírají žádné argumenty. Jsou-li deklarovány jako globální funkce, přebírají jeden argument.  
  
-   Binární operátory, které jsou deklarovány jako členské funkce, přebírají jeden argument. Jsou-li deklarovány jako globální funkce, přebírají dva argumenty.  
  
-   Pokud operátor lze použít jako unární operátor nebo binární operátor (**&**,  **\*** ,  **+** , a  **-** ), můžete použít přetížení každém použití samostatně.  
  
-   Přetížené operátory nemohou mít výchozí argumenty.  
  
-   Všechny přetížené operátory s výjimkou přiřazení (`operator=`) jsou zděděny z odvozených tříd.  
  
-   První argument přetížených operátorů členské funkce je vždy typu třídy objektu, pro který je operátor vyvolán (třída, ve které je operátor deklarován nebo třída odvozená z této třídy). Pro první argument nejsou k dispozici žádné převody.  
  
 Význam libovolného operátoru lze zcela změnit. Význam adresu služby, který obsahuje (**&**), přiřazení (**=**) a operátory volání funkce. Identity, které lze dovolávat pro vestavěné typy, lze také změnit pomocí přetěžování operátoru. Následující čtyři příkazy jsou obvykle při vyhodnocování zcela ekvivalentní:  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 Tuto identitu nelze dovolávat pro typy tříd, které přetěžují operátory. Kromě toho některé požadavky zahrnují použití těchto operátorů pro základní typy, které jsou zmírněny pro přetížené operátory. Například operátor přiřazení/sčítání `+=` vyžaduje, aby byl levý operand při použití na základní typy l-hodnotou. V případě, že je operátor přetížen, neexistuje žádný takový požadavek.  
  
> [!NOTE]
>  V rámci konzistence je při definování přetížených operátorů často nejlepší postupovat podle modelu předdefinovaných typů. Liší-li se významně sémantika přetíženého operátoru od jeho významu v jiných kontextech, může být více matoucí než užitečný.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)