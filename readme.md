Quick Widget
============

A class for rapid widget development in WordPress.

Usage
-----

    function my_register_widgets(  )
    {
    	register_widget('My_Widget');
    }
    add_action('widgets_init', 'my_register_widgets');

    /**
     * Declare the widget
     */
    class My_Widget extends Quick_Widget
    {
        protected $settings = array(
                    'widget_id'     => 'my_widget',
                    'name'	        => 'Example Widget',
                    'description'   => 'Displays some text',
                    'fields'        => array(
                                array(
                                            'name'      => 'Title',
                                            'id'        => 'title',
                                            'type'      => 'text',
                                            'default'   => 'My Super Sweet Widget Title',
                                    ),
                                array(
                                            'name'      => 'Rad Notes',
                                            'desc' 	    => 'This input needs a description.',
                                            'id'        => 'rad_notes',
                                            'type'      => 'textarea',
                                            'default'   => 'Default text for the textarea.',
                                    ),
                            ),
                    'view_callback' => 'my_widget_team_view',
                );
    }
    $team_widget = new My_Widget;

    /**
     * Define the "view" for each widget. Without one, the output will be underwhelming.
     */
    function my_widget_view( $widget, $params, $sidebar )
    {
        extract($params);

        if( !empty($title) )
        {
            echo $sidebar['before_title'] . $title . $sidebar['after_title'];
        }

        if( !empty($rad_notes) )
        {
            echo '<p>', $rad_notes, '</p>';
        }
    }
