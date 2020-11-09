---
ms.openlocfilehash: 2d9b6e29a5ddc71b8f7b78b1e2fe035a8fdbddac
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829790"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="680e8-101">Le flux que vous avez créé au cours de l’exercice précédent utilise l' `$batch` API pour effectuer deux requêtes individuelles à Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="680e8-101">The Flow you created in the previous exercise uses the `$batch` API to make two individual requests to the Microsoft Graph.</span></span> <span data-ttu-id="680e8-102">Le fait `$batch` d’appeler le point de terminaison de cette façon offre des avantages et une flexibilité, mais la véritable puissance du `$batch` point de terminaison est fournie lors de l’exécution de plusieurs demandes vers Microsoft Graph en un seul `$batch` appel.</span><span class="sxs-lookup"><span data-stu-id="680e8-102">Calling the `$batch` endpoint this way provides some benefit and flexibility, but the true power of the `$batch` endpoint comes when executing multiple requests to Microsoft Graph in a single `$batch` call.</span></span> <span data-ttu-id="680e8-103">Dans cet exercice, vous allez étendre l’exemple de création d’un groupe unifié et associer une équipe pour inclure la création de plusieurs canaux par défaut pour l’équipe en une seule `$batch` requête.</span><span class="sxs-lookup"><span data-stu-id="680e8-103">In this exercise, you will extend the example of creating a Unified Group and associating a Team to include creating multiple default Channels for the Team in a single `$batch` request.</span></span>

<span data-ttu-id="680e8-104">Ouvrez [Microsoft Power automatez](https://flow.microsoft.com) -vous dans votre navigateur et connectez-vous avec votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="680e8-104">Open [Microsoft Power Automate](https://flow.microsoft.com) in your browser and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="680e8-105">Sélectionnez le flux que vous avez créé à l’étape précédente, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="680e8-105">Select the Flow you created in the previous step and choose **Edit**.</span></span>

<span data-ttu-id="680e8-106">Choisissez **nouvelle étape** et tapez `Batch` dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="680e8-106">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="680e8-107">Ajoutez l’action du **connecteur de lot MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="680e8-107">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="680e8-108">Sélectionnez les points de suspension et renommez cette action en `Batch POST-channels` .</span><span class="sxs-lookup"><span data-stu-id="680e8-108">Choose the ellipsis and rename this action to `Batch POST-channels`.</span></span>

<span data-ttu-id="680e8-109">Ajoutez le code suivant dans la zone de texte **Body** de l’action.</span><span class="sxs-lookup"><span data-stu-id="680e8-109">Add the following code into the **body** text box of the action.</span></span>

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

<span data-ttu-id="680e8-110">Notez que les trois requêtes ci-dessus utilisent la propriété [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) pour spécifier un ordre séquentiel et chacune exécutera une requête post pour créer un nouveau canal dans la nouvelle équipe.</span><span class="sxs-lookup"><span data-stu-id="680e8-110">Notice the three requests above are using the [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) property to specify a sequence order, and each will execute a POST request to create a new channel in the new Team.</span></span>

<span data-ttu-id="680e8-111">Sélectionnez chaque instance de l' `REPLACE` espace réservé, puis **expression** dans le volet de contenu dynamique.</span><span class="sxs-lookup"><span data-stu-id="680e8-111">Select each instance of the `REPLACE` placeholder, then select **Expression** in the dynamic content pane.</span></span> <span data-ttu-id="680e8-112">Ajoutez la formule suivante dans l' **expression**.</span><span class="sxs-lookup"><span data-stu-id="680e8-112">Add the following formula into the **Expression**.</span></span>

```js
body('Batch_PUT-team').responses[0].body.id
```

![Capture d’écran de l’expression dans le volet de contenu dynamique](./images/dynamic-expression.png)

<span data-ttu-id="680e8-114">Sélectionnez **Enregistrer** , puis **tester** pour exécuter le flux.</span><span class="sxs-lookup"><span data-stu-id="680e8-114">Choose **Save** , then choose **Test** to execute the Flow.</span></span> <span data-ttu-id="680e8-115">Sélectionnez la case d’option **j’exécuterai le déclencheur** , puis choisissez **Enregistrer & test**.</span><span class="sxs-lookup"><span data-stu-id="680e8-115">Select the **I'll perform the trigger** action radio button, then choose **Save & Test**.</span></span> <span data-ttu-id="680e8-116">Entrez un nom de groupe unique dans le champ **nom** sans espaces, puis choisissez **exécuter le flux** pour exécuter le flux.</span><span class="sxs-lookup"><span data-stu-id="680e8-116">Enter a unique group name in the **Name** field without spaces, and choose **Run flow** to execute the Flow.</span></span>

<span data-ttu-id="680e8-117">Une fois le flux démarré, cliquez sur le bouton **Terminer** pour afficher le journal d’activité.</span><span class="sxs-lookup"><span data-stu-id="680e8-117">Once the Flow starts, choose the **Done** button to see the activity log.</span></span> <span data-ttu-id="680e8-118">Une fois le flux terminé, la sortie finale de l' `Batch POST-channels` action est associée à une réponse d’état HTTP 201 pour chaque canal créé.</span><span class="sxs-lookup"><span data-stu-id="680e8-118">When the Flow completes, the final output for the `Batch POST-channels` action has a 201 HTTP Status response for each Channel created.</span></span>

![Capture d’écran du journal d’activité de flux réussi](./images/batch-success.png)

<span data-ttu-id="680e8-120">Accédez à [Microsoft teams](https://teams.microsoft.com) et connectez-vous à l’aide de votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="680e8-120">Browse to [Microsoft Teams](https://teams.microsoft.com) and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="680e8-121">Vérifiez que l’équipe que vous venez de créer apparaît et inclut les trois canaux créés par la `$batch` demande.</span><span class="sxs-lookup"><span data-stu-id="680e8-121">Verify that the team you just created appears and includes the three channels created by the `$batch` request.</span></span>

![Capture d’écran de l’application teams avec la nouvelle équipe et les canaux qui apparaissent](./images/team-channels.png)

<span data-ttu-id="680e8-123">Bien que l’action ci-dessus `Batch POST-channels` ait été implémentée dans ce didacticiel séparément, les appels de création des canaux auraient pu être ajoutés comme appels supplémentaires dans l' `Batch PUT-team` action.</span><span class="sxs-lookup"><span data-stu-id="680e8-123">While the above `Batch POST-channels` action was implemented in this tutorial as a separate action, the calls to create the channels could have been added as additional calls in the `Batch PUT-team` action.</span></span> <span data-ttu-id="680e8-124">Cela aurait créé l’équipe et tous les canaux dans un seul appel de lot.</span><span class="sxs-lookup"><span data-stu-id="680e8-124">This would have created the Team and all Channels in a single batch call.</span></span> <span data-ttu-id="680e8-125">Donnez-lui votre choix.</span><span class="sxs-lookup"><span data-stu-id="680e8-125">Give that a try on your own.</span></span>

<span data-ttu-id="680e8-126">Enfin, n’oubliez pas que les appels de [traitement par lots JSON](https://docs.microsoft.com/graph/json-batching) renvoient un code d’état HTTP pour chaque demande.</span><span class="sxs-lookup"><span data-stu-id="680e8-126">Finally, remember that [JSON Batching](https://docs.microsoft.com/graph/json-batching) calls will return an HTTP status code for each request.</span></span> <span data-ttu-id="680e8-127">Dans un processus de production, vous souhaiterez peut-être combiner post-traitement des résultats avec une [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) action et valider chaque réponse a un code d’état 201 ou compenser tous les autres codes d’état reçus.</span><span class="sxs-lookup"><span data-stu-id="680e8-127">In a production process, you may want to combine post processing of the results with an [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) action and validate each individual response has a 201 status code or compensate for any other status codes received.</span></span>
