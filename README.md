# relationshipType_corrected
Below is the part from line 111 to 126 of civicrm/Contact/BAO/RelationshipType.php:
To fix the issue, the value of $relationshipType->label_b_a is set to
CRM_Utils_Array::value('name_b_a', $params) instead of CRM_Utils_Array::value('label_a_b', $params);

    // action is taken depending upon the mode
    $relationshipType = new CRM_Contact_DAO_RelationshipType();

    $relationshipType->copyValues($params);

    // if label B to A is blank, insert the value label A to B for it
    if (!strlen(trim($strName = CRM_Utils_Array::value('name_b_a', $params)))) {
      $relationshipType->name_b_a = CRM_Utils_Array::value('name_a_b', $params);
    }
    
    //To fix the issue, the value of $relationshipType->label_b_a is set to
      // CRM_Utils_Array::value('name_b_a', $params) instaead of
      //CRM_Utils_Array::value('label_a_b', $params);
     if (!strlen(trim($strName = CRM_Utils_Array::value('label_b_a', $params)))) {
      $relationshipType->label_b_a = CRM_Utils_Array::value('name_b_a', $params);
    }
