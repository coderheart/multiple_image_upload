# multiple_image_upload

 if($_FILES['file_upload1']['tmp_name']==""){ 
            $f_insnt1[]=""; 
            }
            else{
              //$number_of_files_uploaded = count($_FILES['file_upload1']['tmp_name']);
              foreach($_FILES["file_upload1"]["tmp_name"] as $i=>$tmp_name){
              $tmp_file1 = $_FILES['file_upload1']['tmp_name'][$i];
              $target_file1 = basename($_FILES['file_upload1']['name'][$i]);
              $upload_dir1 = "test_img/";
              $file_typ1 = basename($_FILES['file_upload1']['type'][$i]);
              $cur_file1=$upload_dir1."/".$target_file1;
              if($target_file1==""){ $f_insnt1[]="";} else{
              $ran=rand(10000,999999);
              $f_insnt1[]="admin-$ran.".$file_typ1;
              $rename_file1=$upload_dir1."/admin-$ran.".$file_typ1;
              
              if(move_uploaded_file($tmp_file1, $upload_dir1."/".$target_file1)) {
              rename("$cur_file1", "$rename_file1");} 
              else {
              $error = $_FILES['file_upload1']['error'];
              $message = $upload_errors[$error];}
              }
          }
}
	
			$img = "";
			$i=0;
			foreach($f_insnt1 as $hb1){
				$img.=$hb1.',';
			}
