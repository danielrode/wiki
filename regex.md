# Get rid of mid-paragraph line-breaks

	([^\n])\n([^\n])

# Boundary marker

`\b`: The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

# Match but don't select (lookahead/behind/around, negative/positive, context)

Match "ABC" if it is followed by a digit (but do not include the digit in the
match):

	ABC(?=\d)

Match "ABC" if it is NOT followed by a digit (but do not include the digit in
the match):

	ABC(?!\d)
