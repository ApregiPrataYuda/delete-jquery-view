# delete-jquery-view

function delete_store(id) {
	{
    swal({
        title: 'Are you sure?',
        text: "You won't be able to revert this!",
        type: 'warning',
        showCancelButton: true,
        confirmButtonText: 'Yes, delete it!'
    	}).then(function(result) {
        if (result.value) {
           $.ajax({
				url: '<?php echo site_url('master/store/store_controller/delete_data'); ?>/'+id,
                success: function(result)
	        	{
	        		if (result == true) {
	        			swal({
			                title: 'Deleted!',
			                text: "Your data has been deleted.",
			                type: 'success',
			                showCancelButton: false,
			                confirmButtonText: 'OK!'
			            }).then(function(result2) {
                    		if (result2.value){
                    			tbl_store.ajax.reload(null);
                    		}
                    	});
	        		} else {
	        			swal(
	                        'Not Deleted!',
	                        'Your file not deleted.',
	                        'error'
                    	);
	        		}
	        	}
            });
        }
    });
}
}
