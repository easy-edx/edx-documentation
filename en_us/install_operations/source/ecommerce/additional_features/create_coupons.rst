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
   administration tool.

.. Can you point me toward a sandbox so I can complete these instructions?


****************************
Allow Coupon Code Redemption
****************************

You can provide two ways for learners to redeem coupon codes.

.. I wasn't sure what to do with the URLs; please correct as necessary.

* Create an offer landing page.

  An offer landing page presents the offer to the learner and allows the leaner
  to apply the code. The page does not require registration or sign-in. The
  offer landing page provides context and confirms that entering the coupon
  code will enroll the learner in the course.

  .. I'm not sure what "provides context" means above; can you clarify?

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
