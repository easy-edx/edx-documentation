.. _Create Coupons:

########################
Creating Coupon Codes
########################

.. This feature is not in Dogwood.

You can use coupon codes to provide discounted or free course enrollments to
your learners. Two types of coupon codes are available.

* Discount code: These codes offer a discount of up to 99% off the cost of a
  course.
* Enrollment code: These codes offer a 100% discount off the cost of a course.

Both discount codes and enrollment codes can be used in the following ways.

* One time by one user.
* One time by multiple users.
* Multiple times by multiple users.

When you create a coupon code, the E-Commerce service generates an order. The
Invoice Payment Processor module manages these orders and assumes out-of-band
payment for the coupon codes.

The Invoice Payment Modules records the transaction in the Invoice table for
later reconciliation.

.. Would it be correct to say "The Invoice Payment module records the
.. transaction in the Invoice table for later reconciliation." OR "The Invoice
.. Payment Processor module records the transaction in the Invoice table for
.. later reconciliation."?

****************************
Create Coupon Codes
****************************

You create coupon codes by using the coupon administration tool.

#. In your browser, go to ``http://localhost:8002/coupons/`` to open the coupon
   administration tool, and then select **Create Coupon**.
#. On the **Create New Coupon** page, enter the following information.

   .. note::
     All of the following fields are required. After you create a coupon code,
     you can only change the **Valid from** and **Valid until** dates.

   * **Name**: The name you want to give the coupon, such as "Holiday 2015 15%
     Promotion".
   * **Course ID**: The ID of the course that you want to provide the coupon
     for. The course ID is <how does the user know the course ID?>.
   * **Code Type**: Select either **Discount Code** or **Enrollment Code**. For
     more information, see :ref:`Create Coupons`.
   * **Seat Type**: <I've never seen anything in this field, but it's required
     - ? Where do the options come from?>
   * **Category**: Suggested categories for your coupon code. These categories
     can help you keep track of your codes.
   * **Valid from** and **Valid until**: The dates and times when you want to
     start and stop offering the coupon code, respectively. <The time zone is
     set to Universal Coordinated Time (UTC).> You can edit these fields after
     you create the coupon.
   * **Discount Value**: This field is only visible if you select **Discount
     Code** for **Code Type**. Enter the percent or U.S. dollar amount discount
     that you want to offer, then select **Percent** or **Fixed**.

#. (Optional) On the **Create New Coupon** page, enter the following
   information. All of these fields are optional.

   * **Usage Limitations**: The way your coupon code can be used. Options are
     **Can be used once by one customer**, **Can be used once by multiple
     customers**, or **Can be used multiple times by multiple customers**.
   * **Number of codes**: This field is visible if you select **Can be used
     once by one customer**. This value specifies the number of individual
     codes you want to create. Make sure that you create enough codes so that
     each person receives one code.
   * **Code**: This field is visible if you select **Can be used once by
     multiple customers** or **Can be used multiple times by multiple
     customers**. This value specifies the code that recipients enter to redeem
     the coupon code. <You can enter alphanumeric characters as well as
     underscores.> For example, you can enter ``HOLIDAY_15``. If you leave this
     field empty, the system generates a code for you.
   * **Client**: The name of the organization that you create the codes for.
     This organization receives an invoice for the codes you create.
   * **Total Paid**: The cost of the course.

#. Select **Create Coupon**.

When you select **Create Coupon**, a page for your coupon opens. This page
lists the information for your coupon code, including any individual codes that
the system generated as well as the URLs where users can redeem the coupon
codes. To download a .csv file that lists all of this information, select
**Download**.


****************************
Edit Coupon Codes
****************************

You edit coupon codes by using the coupon administration tool.

.. note::
 You can only edit the **Valid from** and **Valid until** information.

#. In your browser, go to ``http://localhost:8002/coupons/`` to open the coupon
   administration tool.
#. On the **Coupon Codes** page, locate the coupon that you want in the table,
   and then select the name of the coupon.
#. On the page for the coupon, select **Edit Coupon**.

   If the coupon has been edited before, the username of the person who last
   edited the coupon is visible, along with the date and time of the last edit.

#. In the **Valid from** or **Valid until** field, enter the date and time that
   you want.
#. Select **Save Changes**.


***********************************
Download Coupon Code Information
***********************************

After you create a coupon code, you can download a .csv file that lists
information such as the name of the coupon code, the URL where a user can
redeem the coupon code, the status of the coupon code, and the user who created
the coupon code. If your coupon code includes multiple individual codes, the
.csv lists information for all of the codes associated with your coupon code.

#. In your browser, go to ``http://localhost:8002/coupons/`` to open the coupon
   administration tool.
#. On the **Coupon Codes** page, locate the coupon that you want in the table,
   and then select the name of the coupon.
#. On the page for the coupon, select **Download**. Your .csv file begins
   downloading automatically.
#. Open the .csv file that you downloaded.


*************************************
Allow Users to Redeem Coupon Codes
*************************************

You can provide two ways for learners to redeem coupon codes.

.. I wasn't sure what to do with the URLs; please correct as necessary. What
.. else does the user have to do to create an offer landing page or redeem
.. endpoint?

* Create an offer landing page.

  An offer landing page presents the offer to the learner and allows the leaner
  to apply the code. The page does not require registration or sign-in. The
  offer landing page provides context and confirms that entering the coupon
  code will enroll the learner in the course.

  To create the landing page, go to
  ``http://localhost:8002/coupons/offer/?code=``.

* Create a redeem endpoint.

  The redeem endpoint adds the course that is associated with the coupon code
  to the learner's basket, applies the coupon code, and completes the order and
  course enrollment. This endpoint requires registration or sign-in. After the
  order is complete, the learner's dashboard opens, and the course the learner
  just enrolled in is visible.

  To create the redeem endpoint, go to
  ``http://localhost:8002/coupons/redeem/?code=``.
